<!DOCTYPE html>
<html lang="en">
<head>

</head>
<body>

<h1>ESPHome Vent-Axia Controller</h1>

<p>A simple ESPHome configuration for controlling <strong>Vent-Axia</strong> MVHR/HRV units (or similar ventilation systems) using an ESP32.</p>

<p>This project lets you add <strong>Boost</strong> and <strong>Purge</strong> modes to your Vent-Axia unit directly from Home Assistant by driving relays connected to the unit's switched live or volt-free inputs.</p>

<h2>Features</h2>

<ul>
    <li>Two switch entities in Home Assistant:
        <ul>
            <li><strong>Vent-Axia Boost</strong> – Temporarily increases fan speed</li>
            <li><strong>Vent-Axia Purge</strong> – Activates high-speed purge mode (ideal for clearing cooking smells, humidity, etc.)</li>
        </ul>
    </li>
    <li>Built-in <strong>Bluetooth Proxy</strong> – turns your ESP32 into an active Bluetooth proxy for Home Assistant (useful for nearby BLE devices or some modern Vent-Axia models with Bluetooth)</li>
    <li>Active BLE scanning enabled</li>
    <li>Safe mode boot button for recovery</li>
    <li>Fully configurable via <code>secrets.yaml</code></li>
    <li>Uses ESP-IDF framework for optimal BLE performance</li>
</ul>

<h2>Hardware Requirements</h2>

<ul>
    <li>ESP32 development board (e.g., ESP32-DevKitC)</li>
    <li>2-channel relay module (or individual relays) - only if your device doesn not accept analog inputs directly from ESP</li>
    <li>Wiring to Vent-Axia's Boost and Purge inputs (usually labeled as switched live or volt-free contacts – check your model's manual)</li>
</ul>

<h3>Example Wiring (Typical)</h3>

<ul>
    <li>GPIO 19 → Relay 1 → Vent-Axia <strong>Purge</strong> input</li>
    <li>GPIO 21 → Relay 2 → Vent-Axia <strong>Boost</strong> input</li>
    <li>Common ground and power as needed</li>
</ul>

<blockquote>
    <p><strong>Warning:</strong> Always verify your unit's wiring diagram and use appropriate isolation/safety measures when working with mains voltage.</p>
</blockquote>

<h2>Installation</h2>

<ol>
    <li>Clone this repository</li>
    <li>Copy <code>secrets.example.yaml</code> to <code>secrets.yaml</code> and fill in your values:
        <pre><code>cp secrets.example.yaml secrets.yaml</code></pre>
    </li>
    <li>Edit <code>secrets.yaml</code> with your WiFi credentials, OTA password, and API encryption key</li>
    <li>(Optional) Change GPIO pins in the main YAML if your relays are connected differently</li>
    <li>Upload via ESPHome dashboard or CLI:
        <pre><code>esphome run vent-axia.yaml</code></pre>
    </li>
</ol>

<h2>secrets.yaml Example</h2>

<pre><code>wifi_ssid: "YourWiFiName"
wifi_password: "YourWiFiPassword"

ota_password: "a_very_strong_password"

api_encryption_key: "your-generated-base64-key-here"
# Generate with: esphome wizard vent-axia.yaml</code></pre>

![ventaxia esp](https://github.com/user-attachments/assets/48b97e08-bfe2-46a5-9a7d-5f44600711c5)

MEV PCB has 5v powersupply which can be used for supplying power to ESP (white USB cable).<br>
Two outputs wired from ESP to correct analog inputs on MEV PCB.<br>
Last thing to do is to set MEV input levels correctly. For me it Vent-Axia Connect settings look like that: <awaiting screenshots><br>


<h2>Useful Automations (Home Assistant)</h2>

<ul>
    <li>Turn on Boost for 30 minutes when humidity spikes</li>
    <li>Activate Purge after cooking (via button or schedule)</li>
    <li>Automatically disable when away from home</li>
</ul>

<h2>Contributing</h2>

<p>Feel free to open issues or pull requests if you:</p>
<ul>
    <li>Add support for more Vent-Axia models</li>
    <li>Include additional sensors (e.g., SHT30 for humidity/temperature)</li>
    <li>Improve documentation or add new features</li>
</ul>

<h2>Support the Project</h2>

<p>If this configuration helped you make your ventilation system smarter, consider supporting further development:</p>

<p>
    <a href="https://buymeacoffee.com/mimikm" class="badge">
        <img src="https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=flat&amp;logo=buy-me-a-coffee&amp;logoColor=black" alt="Buy Me a Coffee">
    </a>
</p>

<p>Direct link: <a href="https://buymeacoffee.com/mimikm">https://buymeacoffee.com/mimikm</a></p>

<p>Thank you! ☕</p>

<h2>License</h2>

<p>MIT License – feel free to use, modify, and share.</p>

</body>
</html>

