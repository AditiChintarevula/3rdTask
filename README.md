##Overview
Interview Insights is a web application designed for students to share and learn from interview experiences, with a touch of motivation. The platform includes sections for viewing interview experiences, sharing new experiences, and contacting the team. The design is responsive, ensuring a seamless experience across various devices.

##Files Included
#index.html: 
The main HTML file containing the structure and content of the web page.
styles.css: The CSS file for styling the web page.
images/: A directory containing image files used in the web page (e.g., logos, icons).
HTML Structure (index.html)
The HTML file is divided into several sections:

Header: Contains the logo and navigation menu.
Main: Divided into multiple sections:
Home: Welcome message and motivational quote.
About: Information about the platform.
Experiences: Displays shared interview experiences.
Submit: A form to share new interview experiences.
Contact: A form to contact the team and social media links.
Footer: Contains a closing message and another motivational quote.
#CSS Styling (styles.css)
The CSS file is organized to provide a clean and modern look:
General styles for the body and text.
Header styles for the logo and navigation menu.
Main section styles for each subsection.
Form styles to ensure consistent appearance.
Responsive design using media queries to adjust styles for different screen sizes.
Social media button styles for enhanced user engagement.

##JavaScript Functionality
JavaScript is used to enhance interactivity and security of the forms on the web page. The JavaScript code includes:

#Input Sanitization: A function sanitizeInput to prevent cross-site scripting (XSS) attacks by converting user input to plain text.
#Form Validation: A function validateForm to ensure all required fields are filled before submission and to sanitize the inputs. This function is attached to both the submit form and the contact form.
JavaScript Code (index.html)
javascript
Copy code
<script>
    // Function to sanitize user input
    function sanitizeInput(input) {
        const div = document.createElement('div');
        div.innerText = input;
        return div.innerHTML;
    }

    // Function to validate form inputs
    function validateForm(event) {
        event.preventDefault();
        
        const name = document.getElementById('name').value;
        const company = document.getElementById('company').value;
        const date = document.getElementById('date').value;
        const experience = document.getElementById('experience').value;

        if (!name || !company || !date || !experience) {
            alert('All fields are required!');
            return false;
        }

        // Sanitize user inputs
        const sanitizedInputs = {
            name: sanitizeInput(name),
            company: sanitizeInput(company),
            date: sanitizeInput(date),
            experience: sanitizeInput(experience)
        };

        // Assuming form submission via AJAX or other means
        console.log('Form submitted with sanitized inputs:', sanitizedInputs);
        alert('Form submitted successfully!');

        // Reset the form
        document.getElementById('submit-form').reset();
        return true;
    }

    document.addEventListener('DOMContentLoaded', () => {
        document.getElementById('submit-form').addEventListener('submit', validateForm);
        document.getElementById('contact-form').addEventListener('submit', validateForm);
    });
</script>
