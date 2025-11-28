🇮🇳 Indian Diet Planner

A fully client-side, intelligent Indian meal planner that generates personalized diet plans based on BMI, BMR, calorie targets, activity level, dietary preference, and budget — using real Indian foods (veg / non-veg).

Live: https://indiandietplanner.vercel.app/

⭐ Overview

Indian Diet Planner is a modern web application built using React + TypeScript, deployed on Vercel, designed to give users a personalized daily meal plan based on:

Age

Sex

Weight

Height

Activity Level

Fitness Goal (Lose / Maintain / Gain)

Diet Preference (Veg / Non-Veg / Both)

Daily Budget

The app uses a nutrition database of real Indian foods (breakfast, lunch, dinner, snack, drinks) and intelligently selects the best food combination under calorie targets & budget.

🏗️ How the Website Is Built (Architecture)
1. Frontend Framework

React/js

TypeScript (strict typing for safety)

Vite / Next.js style bundling (based on your setup)

No backend or database — 100% client-side.

2. Styling & Components

Tailwind CSS for design

Lucide Icons for graphics

Framer Motion for animations & transitions
(smooth page reveal, card animations, button press effects)

3. Deployment

Hosted on Vercel

Fully static export

No API routes

No server code

Instant build & deploy
→ Extremely fast load times

🧠 How It Works — The Entire Logic (Pin to Pin)

This section explains EVERYTHING the site does.

1️⃣ User Inputs Form

When a user fills the form:

Age

Sex

Weight

Height

Activity Level

Goal

Diet Preference

Budget

React stores this using:

const [formData, setFormData] = useState<FormData>();


Each update calls:

updateFormData(key, value)

2️⃣ BMI Calculation
BMI = weight / (height/100)^2


Used to show health category.

3️⃣ BMR Calculation

Using Mifflin–St Jeor Equation:

Male:
BMR = 10W + 6.25H – 5A + 5

Female:
BMR = 10W + 6.25H – 5A – 161

4️⃣ Activity Factor
sedentary:    1.2
light:        1.375
moderate:     1.55
active:       1.725
veryActive:   1.9

5️⃣ Daily Calorie Target
TDEE = BMR × Activity Factor


Then goal adjustment:

lose weight → -400 calories
maintain → +0
gain → +400 calories

6️⃣ Calorie Distribution Across Meals
Meal	%
Breakfast	25%
Lunch	35%
Dinner	30%
Snack	7%
Drink	3%

This creates target calories for each meal.

7️⃣ Budget Distribution
Meal	%
Breakfast	20%
Lunch	35%
Dinner	30%
Snacks	10%
Drinks	5%
8️⃣ The Food Database (FOOD_DATABASE)

You have a large TS file:

120 breakfast items (60 veg, 60 nonveg)

120 lunch items

120 dinner items

60 snack items

60 drink items

Each item includes:

{
 name: "...",
 quantity: "...",
 calories: 210,
 protein: 8,
 carbs: 34,
 fats: 4,
 fiber: 3,
 price: 30,
 type: "veg" | "nonveg",
 recipe: "..."
}


100% real Indian food — no AI-generated foods.

9️⃣ Meal Selection Logic (The Smart Part)

Function used:

selectBestFood(foodArray, targetCalories, maxBudget, dietPreference)

It does 4 things:
✔ 1. Filters by diet preference

veg

nonveg

both → 50/50 randomization (creates variety)

✔ 2. Checks budget

Item must be ≤ budget.

✔ 3. Picks closest-calorie item
diff = abs(food.calories - targetCalories)


Closest diff = selected.

✔ 4. Returns the BEST MATCHED dish
🔟 Meal Plan Construction
mealPlan = {
 breakfast: selectBestFood(...),
 lunch: selectBestFood(...),
 dinner: selectBestFood(...),
 snack: selectBestFood(...),
 drink: selectBestFood(...)
}

1️⃣1️⃣ Nutrient Summary Calculations

Totals:

totalCalories
totalProtein
totalCarbs
totalFats
totalFiber
totalCost


Displayed beautifully in your summary cards.

1️⃣2️⃣ UI Rendering & Animations
Animations:

fade-in

slide-up

scale pop

delay-based stagger effects

Using:

<motion.div initial={{...}} animate={{...}} />


Makes the site look modern & premium.

1️⃣3️⃣ Why No Backend?

Because:

All logic runs client-side

FOOD_DATABASE is static

No login / signup

No storage

High performance

📁 Project Folder Structure (Ideal)
src/
 ├── components/
 │     └── Index.tsx
 │
 ├── data/
 │     └── FOOD_DATABASE.ts
 │
 ├── styles/
 │     └── globals.css
 │
 ├── assets/
 │
 └── main.tsx

🛠️ Technologies Used

React

TypeScript

Tailwind CSS

Framer Motion

Lucide Icons

Vercel Deployment

🚀 How to Run Locally
1. Clone the repo
git clone https://github.com/yourusername/indiandietplanner.git
cd indiandietplanner

2. Install dependencies
npm install

3. Start development server
npm run dev


Website opens at:

http://localhost:8081/

4. Build for production
npm run build

🎯 Key Features
✔ Intelligent Indian meal generation
✔ Real foods — no AI generated items
✔ Pure client-side
✔ Smooth animations
✔ Fully responsive
✔ Very fast (Vercel + static build)
✔ Complex nutrition calculations
✔ Works offline after load
