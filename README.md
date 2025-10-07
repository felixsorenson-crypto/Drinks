# Drinks
<!DOCTYPE html>
<html lang="sv">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Min Hemmabar 🍸</title>
<style>
  body { font-family: Arial; max-width: 600px; margin: auto; padding: 20px; }
  h1 { text-align: center; }
  .ingredient { display: inline-block; width: 45%; }
  .drink { background: #f3f3f3; margin: 8px 0; padding: 8px; border-radius: 5px; }
</style>
</head>
<body>
<h1>Min Hemmabar 🍸</h1>
<p>Bocka i vad du har hemma:</p>

<div id="ingredients"></div>

<h2>Drinkar du kan göra:</h2>
<div id="result"></div>

<script>
// Lista över ingredienser
const ingredients = ["Vodka", "Gin", "Rom", "Tequila", "Whiskey", "Triple sec", "Limejuice", "Tonic", "Cola", "Sodavatten", "Sockerlag", "Grädde", "Kahlúa"];

// Drinkrecept
const drinks = [
  { name: "Gin & Tonic", ingredients: ["Gin", "Tonic"] },
  { name: "Rum & Cola", ingredients: ["Rom", "Cola"] },
  { name: "Margarita", ingredients: ["Tequila", "Triple sec", "Limejuice"] },
  { name: "Whiskey Sour", ingredients: ["Whiskey", "Limejuice", "Sockerlag"] },
  { name: "White Russian", ingredients: ["Vodka", "Kahlúa", "Grädde"] },
  { name: "Vodka Soda", ingredients: ["Vodka", "Sodavatten"] },
];

// Skapa checkboxar
const ingredientDiv = document.getElementById("ingredients");
ingredients.forEach(i => {
  const label = document.createElement("label");
  label.className = "ingredient";
  label.innerHTML = `<input type="checkbox" value="${i}"> ${i}`;
  ingredientDiv.appendChild(label);
});

const resultDiv = document.getElementById("result");

// Lyssna på ändringar
ingredientDiv.addEventListener("change", updateDrinks);

function updateDrinks() {
  const selected = [...document.querySelectorAll("input:checked")].map(c => c.value);
  resultDiv.innerHTML = "";

  drinks.forEach(drink => {
    const hasAll = drink.ingredients.every(ing => selected.includes(ing));
    if (hasAll) {
      const div = document.createElement("div");
      div.className = "drink";
      div.textContent = drink.name + " ✅";
      resultDiv.appendChild(div);
    }
  });

  if (resultDiv.innerHTML === "") {
    resultDiv.textContent = "Inga kompletta drinkar än 😅";
  }
}
</script>
</body>
</html>
