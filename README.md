# Iteration 2: Adding BMI Categories & Image Display

## **📖 Project Overview**
This is the **second version** of the BMI Calculator project. In this version, the application **dynamically displays one of four category images** (Underweight, Normal, Overweight, or Obese) based on the user's **calculated BMI result**.

---

## **🚀 Features Implemented**
✅ **User input fields** for weight (kg) and height (cm).  
✅ **Dynamic BMI calculation** and clear result display.  
✅ **Automatic BMI categorization** into Underweight, Normal, Overweight, or Obese.  
✅ **Image display** based on the **BMI category**.  

---

## **💻 Code Implementation**
- The **BMI calculation** remains the same as in Iteration 1.  
- A **new function** was added to determine the **BMI category** and select the correct image.  

**Example Code (Updated BMI Category & Image Selection in `index.php`)**:
```php
function getBMICategory($bmi) {
    if ($bmi < 18.5) return ["Underweight", "underweight.png"];
    elseif ($bmi < 24.9) return ["Normal weight", "normal.png"];
    elseif ($bmi < 29.9) return ["Overweight", "overweight.png"];
    else return ["Obese", "obese.png"];
}

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $weight = $_POST["weight"];
    $height = $_POST["height"];
    
    if ($weight > 0 && $height > 0) {
        $heightInMeters = $height / 100;
        $bmi = $weight / ($heightInMeters * $heightInMeters);
        $bmi = round($bmi, 1);
        
        list($category, $image) = getBMICategory($bmi);

        echo "<div class='result'>
                <div>Your BMI is: $bmi</div>
                <div>Category: $category</div>
                <img src='$image' alt='$category' width='100px'>
              </div>";
    } else {
        echo "<div class='result' style='color: red;'>Please enter valid numbers.</div>";
    }
}
Category	        BMI range
Underweight	      BMI < 18.5
Normal	              BMI 18.5 - 24.9
Overweight	      BMI 25 - 29.9
Obese	              BMI ≥ 30

Challenges:
Ensuring the correct image displays dynamically, Solution: Used a PHP function to map BMI ranges to image files
Handling user input errors, Solution: Implemented form validation to prevent empty or invalid values
UI looked too simple, Solution: Added CSS styling for better visual appeal

## **🚀  Setup Instructions**
1. Clone or download this repository to your local machine.
2. Ensure you have a PHP server (e.g., XAMPP, WAMP) set up.
3. Place the files in your web server's directory (e.g., htdocs for XAMPP).
4. Add the provided images (underweight.png, normal.png, overweight.png, obese.png) to the same directory as the main code file.
5. Open the application in your browser

## **📌  Setup Instructions**
1. Enter your weight (kg) and height (cm).
2. Click "Calculate BMI".
3. View your BMI result and category along with the corresponding image.

## **📌 Future Improvements**
Additional UI enhancements.
Localization for different languages.
Responsive design improvements.
