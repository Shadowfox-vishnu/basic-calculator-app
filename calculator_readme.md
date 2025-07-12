# Basic Calculator Application

A modern, feature-rich calculator application built with HTML, CSS, and JavaScript. This calculator provides intuitive user interaction and clear display of results with a beautiful dark theme design.

## 🚀 Features

### **Core Functionality**
- **Basic Arithmetic Operations**: Addition (+), Subtraction (-), Multiplication (×), Division (÷)
- **Additional Operations**: Modulo (%) for remainder calculations
- **Decimal Support**: Full decimal number support with proper formatting
- **Clear Display**: Large, easy-to-read display with previous operation history
- **Error Handling**: Prevents division by zero and handles invalid operations

### **User Interface**
- **Modern Dark Theme**: Sleek dark design with orange accent colors
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Button Animations**: Smooth hover effects and press animations
- **History Panel**: Shows last 5 calculations for reference
- **Intuitive Layout**: Standard calculator layout with clear button organization

### **Advanced Features**
- **Keyboard Support**: Full keyboard input support
- **Real-time Updates**: Display updates instantly as you type
- **Number Formatting**: Large numbers are formatted with commas for readability
- **Session Persistence**: Calculator state is maintained during use

## 📁 File Structure

```
.android/
├── calculator.html        # Main calculator application
├── CALCULATOR_README.md  # This documentation
├── index.html            # Login page
├── welcome.html          # Welcome page
└── README.md            # Login system documentation
```

## 🎯 How to Use

### **Basic Operations**
1. **Open** `calculator.html` in your web browser
2. **Enter Numbers**: Click number buttons or use keyboard (0-9)
3. **Choose Operation**: Click +, -, ×, ÷, or % buttons
4. **Calculate**: Press = button or Enter key
5. **Clear**: Press AC button or Escape key

### **Keyboard Shortcuts**
- **Numbers**: 0-9 keys
- **Decimal**: . (period) key
- **Operations**: +, -, *, /, % keys
- **Equals**: Enter or = key
- **Clear All**: Escape key
- **Delete Last**: Backspace key

### **Button Functions**
- **AC**: Clear All - resets calculator completely
- **DEL**: Delete Last - removes last entered digit
- **÷**: Division
- **×**: Multiplication
- **-**: Subtraction
- **+**: Addition
- **%**: Modulo (remainder)
- **=**: Calculate result
- **.**: Decimal point

## 💻 Source Code Explanation

### **Calculator Class Structure**

```javascript
class Calculator {
    constructor() {
        this.previousOperand = '';    // Previous number in operation
        this.currentOperand = '0';    // Current number being entered
        this.operation = undefined;   // Current operation (+,-,×,÷,%)
        this.history = [];           // Calculation history
    }
}
```

### **Core Methods**

#### **Number Input**
```javascript
appendNumber(number) {
    if (number === '.' && this.currentOperand.includes('.')) return;
    if (this.currentOperand === '0' && number !== '.') {
        this.currentOperand = number;
    } else {
        this.currentOperand = this.currentOperand.toString() + number;
    }
}
```

#### **Operation Selection**
```javascript
chooseOperation(operation) {
    if (this.currentOperand === '0') return;
    if (this.previousOperand !== '') {
        this.compute();  // Auto-compute if operation already selected
    }
    this.operation = operation;
    this.previousOperand = this.currentOperand;
    this.currentOperand = '0';
}
```

#### **Calculation Logic**
```javascript
compute() {
    let computation;
    const prev = parseFloat(this.previousOperand);
    const current = parseFloat(this.currentOperand);
    
    if (isNaN(prev) || isNaN(current)) return;
    
    switch (this.operation) {
        case '+': computation = prev + current; break;
        case '-': computation = prev - current; break;
        case '×': computation = prev * current; break;
        case '÷': 
            if (current === 0) {
                alert('Cannot divide by zero!');
                return;
            }
            computation = prev / current; 
            break;
        case '%': computation = prev % current; break;
        default: return;
    }
    
    this.currentOperand = computation;
    this.operation = undefined;
    this.previousOperand = '';
}
```

### **Display Formatting**

```javascript
getDisplayNumber(number) {
    const stringNumber = number.toString();
    const integerDigits = parseFloat(stringNumber.split('.')[0]);
    const decimalDigits = stringNumber.split('.')[1];
    
    let integerDisplay;
    if (isNaN(integerDigits)) {
        integerDisplay = '0';
    } else {
        integerDisplay = integerDigits.toLocaleString('en', {
            maximumFractionDigits: 0
        });
    }
    
    if (decimalDigits != null) {
        return `${integerDisplay}.${decimalDigits}`;
    } else {
        return integerDisplay;
    }
}
```

## 🎨 CSS Features

### **Modern Design**
- **Dark Theme**: Professional dark background (#1a1a1a)
- **Gradient Background**: Beautiful purple-blue gradient
- **Rounded Corners**: Modern 20px border radius
- **Box Shadows**: Depth and elevation effects

### **Button Styling**
```css
.btn {
    background: #333;
    color: white;
    border: none;
    border-radius: 10px;
    padding: 20px;
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
}

.btn:hover {
    background: #444;
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}
```

### **Color Coding**
- **Numbers**: Dark gray (#333)
- **Operators**: Orange (#ff9500)
- **Equals**: Blue (#007aff)
- **Clear/Delete**: Red (#ff3b30)

### **Responsive Design**
```css
@media (max-width: 400px) {
    .calculator { padding: 15px; }
    .btn { padding: 15px; font-size: 16px; }
    .current-operand { font-size: 28px; }
}
```

## 🔧 Technical Implementation

### **Event Handling**
- **Click Events**: All buttons have onclick handlers
- **Keyboard Events**: Full keyboard support with event listeners
- **Animation Events**: Button press animations with CSS classes

### **State Management**
- **Current Operand**: Number being entered
- **Previous Operand**: Number from previous operation
- **Operation**: Current mathematical operation
- **History**: Array of recent calculations

### **Error Prevention**
- **Division by Zero**: Alert message and operation cancellation
- **Invalid Input**: Prevents multiple decimal points
- **NaN Handling**: Graceful handling of invalid numbers

## 📱 Browser Compatibility

- **Chrome**: Full support (recommended)
- **Firefox**: Full support
- **Safari**: Full support
- **Edge**: Full support
- **Mobile Browsers**: Responsive design works on all devices

## 🚀 Performance Features

- **Efficient DOM Updates**: Minimal DOM manipulation
- **Smooth Animations**: CSS transitions for better UX
- **Memory Management**: Proper cleanup of event listeners
- **Fast Calculations**: Optimized mathematical operations

## 🎯 Usage Examples

### **Basic Calculation**
1. Enter: `5`
2. Press: `+`
3. Enter: `3`
4. Press: `=`
5. Result: `8`

### **Decimal Calculation**
1. Enter: `10.5`
2. Press: `×`
3. Enter: `2.5`
4. Press: `=`
5. Result: `26.25`

### **Complex Operation**
1. Enter: `100`
2. Press: `÷`
3. Enter: `3`
4. Press: `=`
5. Result: `33.333333333333336`

## 🔧 Customization

### **Changing Colors**
Modify CSS variables in the `<style>` section:

```css
:root {
    --primary-color: #ff9500;
    --secondary-color: #007aff;
    --background-color: #1a1a1a;
    --display-color: #2d2d2d;
}
```

### **Adding New Operations**
Extend the `compute()` method:

```javascript
case '^':  // Power operation
    computation = Math.pow(prev, current);
    break;
case '√':  // Square root
    computation = Math.sqrt(current);
    break;
```

### **Modifying History**
Change the history limit in the `compute()` method:

```javascript
if (this.history.length > 10) {  // Change from 5 to 10
    this.history.pop();
}
```

## 🐛 Troubleshooting

### **Common Issues**

1. **Calculator not responding**: Check browser console for JavaScript errors
2. **Display not updating**: Ensure all event handlers are properly connected
3. **Keyboard not working**: Verify keyboard event listeners are active
4. **Styling issues**: Clear browser cache and reload page

### **Debug Mode**
Add this to browser console for debugging:

```javascript
// View calculator state
console.log(calculator);

// Clear calculator
calculator.clear();

// Check current values
console.log('Current:', calculator.currentOperand);
console.log('Previous:', calculator.previousOperand);
console.log('Operation:', calculator.operation);
```

## 🔮 Future Enhancements

- **Scientific Functions**: Trigonometry, logarithms, exponentials
- **Memory Functions**: M+, M-, MR, MC buttons
- **History Export**: Save calculation history to file
- **Theme Switcher**: Light/dark theme toggle
- **Unit Converter**: Built-in unit conversion
- **Graphing**: Basic function plotting
- **Voice Input**: Speech-to-text for calculations

## 📄 License

This calculator application is open source and available under the MIT License.

---

**Enjoy calculating! 🧮✨** 