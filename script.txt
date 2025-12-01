document.addEventListener('DOMContentLoaded', function () {
    const form = document.getElementById('myForm');

    if (!form) {
        console.error("Form with ID 'myForm' not found!");
        return;
    }

    // Corrected IDs to match HTML
    const fullNameInput = document.getElementById('fullName');
    const emailInput = document.getElementById('email');
    const phoneInput = document.getElementById('phone'); // Corrected ID
    const passwordInput = document.getElementById('password');
    const confirmPasswordInput = document.getElementById('confirmPassword');

    // Corrected IDs for error messages
    const nameError = document.getElementById('nameError');
    const emailError = document.getElementById('emailError');
    const phoneError = document.getElementById('phoneError');
    const passwordError = document.getElementById('passwordError');
    const confirmPasswordError = document.getElementById('confirmPasswordError');

    form.addEventListener('submit', (e) => {
        e.preventDefault();

        const fullName = fullNameInput.value.trim();
        const email = emailInput.value.trim();
        const phone = phoneInput.value.trim();
        const password = passwordInput.value.trim();
        const confirmPassword = confirmPasswordInput.value.trim();

        let isValid = true;

        // Full Name Validation
        if (fullName.length < 5) {
            nameError.textContent = 'Name must be at least 5 characters long.';
            isValid = false;
        } else {
            nameError.textContent = '';
        }

        // Email Validation
        if (!email.includes('@') || !email.includes('.')) {
            emailError.textContent = 'Invalid email address.';
            isValid = false;
        } else {
            emailError.textContent = '';
        }

        // Phone Number Validation
        if (!/^\d{10}$/.test(phone) || phone === '1234567890') {
            phoneError.textContent = 'Invalid phone number.';
            isValid = false;
        } else {
            phoneError.textContent = '';
        }

        // Password Validation
        if (password.length < 8 || password.toLowerCase() === 'password' || password === fullName) {
            passwordError.textContent = 'Password must be at least 8 characters and not be "password" or your name.';
            isValid = false;
        } else {
            passwordError.textContent = '';
        }

        // Confirm Password Validation
        if (password !== confirmPassword) {
            confirmPasswordError.textContent = 'Passwords do not match.';
            isValid = false;
        } else {
            confirmPasswordError.textContent = '';
        }

        if (isValid) {
            alert('Form submitted successfully! ✅');
            form.reset(); // Clear form after successful submission
        }
    });
});
