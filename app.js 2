function save() {
  localStorage.setItem("wardrobe", JSON.stringify(wardrobe));
}

// ADD ITEM
function addItem() {
  let name = document.getElementById("name").value;
  let category = document.getElementById("category").value;
  let file = document.getElementById("image").files[0];

  if (!name || !category) return;

  let item = {
    name,
    category,
    image: file ? URL.createObjectURL(file) : ""
  };

  wardrobe.push(item);
  save();
  renderWardrobe();
}

// RENDER WARDROBE
function renderWardrobe() {
  let grid = document.getElementById("wardrobeGrid");
  if (!grid) return;

  grid.innerHTML = "";

  wardrobe.forEach(item => {
    grid.innerHTML += `
      <div class="card">
        <img src="${item.image}" style="width:100%; border-radius:10px;">
        <p>${item.name}</p>
        <small>${item.category}</small>
      </div>
    `;
  });
}

// SIMPLE AI OUTFIT GENERATOR
function generateOutfit() {
  if (wardrobe.length < 3) return;

  let shuffled = [...wardrobe].sort(() => 0.5 - Math.random());

  let outfit = shuffled.slice(0, 3);

  document.getElementById("outfitResult").innerHTML =
    formatOutfit(outfit);
}

function generateRandomOutfit() {
  if (wardrobe.length < 3) return;

  let shuffled = [...wardrobe].sort(() => 0.5 - Math.random());

  let outfit = shuffled.slice(0, 3);

  document.getElementById("homeOutfit").innerHTML =
    formatOutfit(outfit);
}

function formatOutfit(items) {
  return `
    <div class="card">
      <h3>Your Outfit</h3>
      <p>${items.map(i => i.name).join(" + ")}</p>
    </div>
  `;
}

// INIT
renderWardrobe();
