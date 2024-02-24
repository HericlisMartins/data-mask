1. 
The script creates a "Mask" block on top of the actual input values, potentially compromising the integrity of values passed to the input and affecting the visual appearance during navigation without script execution.

    .mask {
        position: absolute;
        /* ... other styles ... */
    }

    <div class="masked_input">
        <div class="mask" data-mask="DD/MM-YYYY" data-autofill="/-">
            <span class="copy"></span>
            <span class="mask_partial"></span>
        </div>
    </div>
    
Instead, a placeholder could be used as a native solution:

    <input type="text" id="dob" placeholder="DD/MM/YYYY" maxlength="10">

2.
The script fails to handle alphabetic characters properly due to the regex used for masking.

    const regex = new RegExp(`\\${char}`, 'g');

A more suitable regex to validate and handle alphabetic characters could be:

    value = value.replace(/\D/g, '');


3.

The script lacks date verification. Introducing a date validation function is suggested to ensure the entered date is in the correct format.


function validateDate(dateString) {
    const regex = /^\d{2}\/\d{2}\/\d{4}$/;
    if (!regex.test(dateString)) return false;
    // ... additional validation logic ...
}