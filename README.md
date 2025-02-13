# Iteration 3: Implementing a GUI & Enhancing User Experience

## **📖 Overview**
In **Iteration 3**, we transformed the BMI Calculator into a **Graphical User Interface (GUI)** using **CSS, Bootstrap, and JavaScript validation**. This version enhances usability and responsiveness, making the application more visually appealing and user-friendly.

---

## **🚀 Features Implemented**
✅ **Styled UI with CSS & Bootstrap** for modern design.  
✅ **JavaScript validation** to prevent invalid inputs before submission.  
✅ **Dynamic color bar** that visually represents the BMI range.  
✅ **Reference category section** with images for better BMI understanding.  
✅ **Fully responsive design** for mobile and desktop compatibility.  

---

## **🛠️ How It Works**
1. The user enters **weight (kg)** and **height (cm)** in the provided input fields.  
2. Upon clicking **"Calculate BMI"**, the **PHP script** processes the input.  
3. The **BMI is computed** using the formula:  
   \[
   BMI = \frac{\text{weight (kg)}}{\text{height (m)}^2}
   \]
4. The result is displayed **with a corresponding BMI category, image, and a color-coded scale**.  
5. **JavaScript validation** ensures users enter only valid numbers before submission.  

---

## **💻 Code Implementation**
- **CSS & Bootstrap** improve the UI.
- **JavaScript validation** prevents incorrect values.
- **PHP handles BMI calculation and category assignment**.

### **Example Code (JavaScript Validation in `script.js`)**
```js
document.getElementById("bmiForm").addEventListener("submit", function(event) {
    let weight = document.getElementById("weight").value;
    let height = document.getElementById("height").value;
    if (weight <= 0 || height <= 0) {
        alert("Please enter valid numbers.");
        event.preventDefault();
    }
});

## **💻 Example Code**
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
        $bmi = round($weight / ($heightInMeters * $heightInMeters), 1);
        
        list($category, $image) = getBMICategory($bmi);

        echo "<div class='result'>
                <div>Your BMI is: $bmi</div>
                <div>Category: $category</div>
                <img src='images/$image' alt='$category' width='100px'>
              </div>";

        echo "<script>document.getElementById('bmiScale').style.background = '#2ecc71';</script>";
    } else {
        echo "<div class='result' style='color: red;'>Please enter valid numbers.</div>";
    }
}

## **📌 Installation & Usage**
1. Ensure you have a PHP server (e.g., XAMPP, WAMP).
2. Place all files in the server’s public directory (e.g., htdocs for XAMPP).
3. Open index.php in a browser via:
http://localhost/BMI_Calculator
4. Enter weight and height, then submit the form to see your BMI result, category, and image.

##  **📌 Known Issues & Future Improvements**
##  **✅ Improve UI feedback:** Display real-time BMI results without page reload using JavaScript.
##  **✅ Better accessibility:** Adding voice-assisted output for visually impaired users.
##  **✅ Dark mode support:** Adding a toggle for dark mode.
##  **✅ Localization:** Support for multiple languages.
