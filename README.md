# Astrology-website
Astrology website, personalized readings
document.getElementById("horoscope-form").addEventListener("submit", function(event) {
    event.preventDefault(); // This stops the form from submitting the traditional way.

    var sign = document.getElementById("sign").value; // Get the sign from the form

    // Now we'll set up the request to the Aztro API.
    var apiUrl = 'https://aztro.sameerkumar.website/';
    var options = {
        method: 'POST',
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        body: 'sign=' + sign + '&day=today'
    };

    // Send the request
    fetch(apiUrl, options)
        .then(response => response.json()) // Convert the response to JSON
        .then(data => {
            // Now we put the horoscope into the HTML
            document.getElementById("horoscope-result").innerText = data.description;
        })
        .catch(error => {
            // If there's an error, log it to the console.
            console.error('Error:', error);
        });
});
