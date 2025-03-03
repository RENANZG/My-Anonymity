<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Protocols Comparison: XMPP vs Matrix vs MQTT</title>
<style>
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 20px 0;
    }
    table, th, td {
      border: 1px solid #dddddd;
    }
    th, td {
      padding: 12px;
      text-align: left;
    }
    th {
      background-color: #f4f4f4;
    }
</style>
</head>
<body>

  <h1>Protocols Comparison: XMPP vs Matrix vs MQTT</h1>

  <table>
    <thead>
      <tr>
        <th>Feature</th>
        <th>XMPP</th>
        <th>Matrix</th>
        <th>MQTT</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Protocol Type</strong></td>
        <td>XML-based messaging protocol</td>
        <td>Real-time communication protocol</td>
        <td>Lightweight messaging protocol</td>
      </tr>
      <tr>
        <td><strong>Primary Use Case</strong></td>
        <td>Instant messaging, presence</td>
        <td>Decentralized messaging, VoIP</td>
        <td>IoT, M2M communication</td>
      </tr>
      <tr>
        <td><strong>Architecture</strong></td>
        <td>Client-server</td>
        <td>Decentralized (federated)</td>
        <td>Client-broker</td>
      </tr>
      <tr>
        <td><strong>Scalability</strong></td>
        <td>Scalable with federated servers</td>
        <td>Highly scalable with federation</td>
        <td>Highly scalable with broker clusters</td>
      </tr>
      <tr>
        <td><strong>Message Format</strong></td>
        <td>XML</td>
        <td>JSON</td>
        <td>Binary (Optimized for low bandwidth)</td>
      </tr>
      <tr>
        <td><strong>Security</strong></td>
        <td>Supports TLS, SASL, and end-to-end encryption (OMEMO)</td>
        <td>Supports TLS and end-to-end encryption (Olm, Megolm)</td>
        <td>Supports TLS, username/password, and client certificates</td>
      </tr>
      <tr>
        <td><strong>Offline Messaging</strong></td>
        <td>Supported</td>
        <td>Supported</td>
        <td>Supported (via retained messages)</td>
      </tr>
      <tr>
        <td><strong>Quality of Service (QoS)</strong></td>
        <td>Basic message delivery with presence notifications</td>
        <td>Basic message delivery with event notifications</td>
        <td>Three levels: 0 (at most once), 1 (at least once), 2 (exactly once)</td>
      </tr>
      <tr>
        <td><strong>Supported Clients</strong></td>
        <td>Wide range of clients (e.g., Pidgin, Gajim)</td>
        <td>Wide range of clients (e.g., Element, FluffyChat)</td>
        <td>Numerous IoT clients (e.g., Eclipse Paho, Mosquitto)</td>
      </tr>
      <tr>
        <td><strong>Extensibility</strong></td>
        <td>Highly extensible with XEPs (XMPP Extension Protocols)</td>
        <td>Extensible via custom events and modules</td>
        <td>Extensible with custom topics and payloads</td>
      </tr>
      <tr>
        <td><strong>License</strong></td>
        <td>Open standard (IETF RFCs)</td>
        <td>Open standard (Matrix.org)</td>
        <td>Open standard (OASIS)</td>
      </tr>
    </tbody>
  </table>

</body>
</html>