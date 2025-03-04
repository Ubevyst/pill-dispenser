<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pill Dispenser Control</title>
    <script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
</head>
<body>
    <h2>Pill Dispenser Control</h2>
    <button onclick="dispensePill()">Dispense Pill</button>
    <p id="status">Status: Waiting...</p>

    <script>
        const broker = "wss://f8ce84ba874c4225b531260f66793bc4.s1.eu.hivemq.cloud:8884/mqtt"; // Your MQTT broker
        const topic = "pill/dispenser"; 

        const client = mqtt.connect(broker, {
            username: "your-username", // Replace with your HiveMQ username
            password: "your-password", // Replace with your HiveMQ password
        });

        client.on("connect", () => {
            document.getElementById("status").innerText = "Connected to MQTT Broker!";
        });

        function dispensePill() {
            client.publish(topic, "DISPENSE");
            document.getElementById("status").innerText = "Pill Dispensed!";
        }
    </script>
</body>
</html>
