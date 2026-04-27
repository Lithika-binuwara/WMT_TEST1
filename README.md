1. Backend Updates (Node.js & Express)

Step A: Update the Data Model
Locate your item model file (typically models/itemModel.js or models/Item.js). You must add the new field to the Mongoose schema so the database knows to accept it.

Action: Add countryOfOrigin to the schema object.

Code logic:

JavaScript
const itemSchema = new mongoose.Schema({
  name: { type: String, required: true },
  // ... existing fields
  countryOfOrigin: { type: String, required: true } // New Field
});

Step B: Update the Controller Logic
Locate the controller file (typically controllers/itemController.js) that handles the logic for creating and retrieving items.

Action: In the function that handles creating a new item (e.g., createItem), ensure the backend extracts countryOfOrigin from the request body (req.body).


Action: If there is an update function, ensure it also includes this new field.

2. Frontend Updates (React)

Step A: Update the "Add Item" Form
Locate the component responsible for adding items (e.g., AddItem.jsx or CreateItem.jsx).

State Management: Create a new state variable to hold the input value:
const [countryOfOrigin, setCountryOfOrigin] = useState('');


Form Input: Add a new label and input field in the JSX.

HTML
<label>Country of Origin:</label>
<input 
  type="text" 
  value={countryOfOrigin} 
  onChange={(e) => setCountryOfOrigin(e.target.value)} 
/>

API Call: Ensure that when the "Submit" button is clicked, the countryOfOrigin value is included in the object sent to the backend via axios or fetch.

Step B: Update the Home Page Display
You must ensure the new data is visible to the user once it has been saved.

Action: Open the component that lists items (e.g., Home.jsx or ItemList.jsx).

Action: Inside the loop (usually a .map() function) that renders the items, add a line to display the new field.

Example: <p>Origin: {item.countryOfOrigin}</p>

npm install express mongoose cors dotenv
npm install nodemon --save-dev

git init
git add .
git commit -m "initial commit"
git remote add origin YOUR_REPO_URL
git push -u origin main
