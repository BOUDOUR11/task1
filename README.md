# task1
web-based Age Calculator using JavaScript to calculate users' ages based on their submitted date of birth, month, and year. JavaScript's built-in date and time functions
document.getElementById('ageCalculatorForm').addEventListener('submit', function(event) {
    event.preventDefault();
  
    // Get user input values
    const day = parseInt(document.getElementById('dob').value);
    const month = parseInt(document.getElementById('mob').value) - 1; // JavaScript months are 0-indexed (0 = January)
    const year = parseInt(document.getElementById('yob').value);
  
    // Validate input
    if (isNaN(day) || isNaN(month) || isNaN(year)) {
      alert('Please enter valid date of birth.');
      return;
    }
  
    // Create Date objects for current date and user's birthday
    const today = new Date();
    const birthday = new Date(year, month, day);
  
    // Calculate age
    let age = today.getFullYear() - birthday.getFullYear();
    const monthDiff = today.getMonth() - birthday.getMonth();
    
    if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birthday.getDate())) {
      age--;
    }
  
    // Display the result
    document.getElementById('result').innerHTML = `Your age is ${age} years.`;
  });
  
