<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Identity and Privacy Intersection</title>
<style>
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 8px;
    }
    th {
      background-color: #f2f2f2;
    }
</style>
</head>
<body>

<h2>Identity and Privacy Intersection</h2>

<table border="1">
  <thead>
  <tr>
    <th>IDENTITY / PRIVACY LEVEL</th>
    <th>PUBLIC</th>
    <th>SEMI-PRIVATE</th>
    <th>PRIVATE</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>TRUE IDENTITY</td>
    <td>
    <ul>
      <li>Shopping in a store with visible face and card payment.</li>
      <li>IP address logged when browsing websites openly.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Logging into online accounts (e.g., Google account) with location/IP tracked.</li>
      <li>Sharing location-tagged content on social media.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Conducting private meetings at home without connected devices.</li>
      <li>Using personal devices offline to avoid external tracking.</li>
    </ul>
    </td>
  </tr>
  <tr>
    <td>PSEUDONYMITY</td>
    <td>
    <ul>
      <li>Posting on forums or blogs with a pseudonym, where IP is visible to the site admin.</li>
      <li>Engaging in geotagged cryptocurrency transactions under a pseudonym.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Participating in social media using a pseudonymous account.</li>
      <li>Browsing websites with pseudonymous accounts but without anonymizing IP.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Using encrypted forums with non-identifiable pseudonyms.</li>
      <li>Making cryptocurrency transactions using obfuscated wallets and anonymized IP addresses.</li>
    </ul>
    </td>
  </tr>
  <tr>
    <td rowspan="2">ANONYMITY</td>
    <td>
    <ul>
      <li>Reading public news websites without an account but with IP tracking by the site.</li>
      <li>Donating anonymously but with potential camera footage at the location.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Browsing content through Tor but leaving identifiable traces, like cookies or reused pseudonyms.</li>
      <li>Accessing websites through Tor to mask IP and location fully.</li>
    </ul>
    </td>
    <td>
    <ul>
      <li>Posting content on anonymous forums via Tor or I2P.</li>
      <li>Uploading untraceable files using services like OnionShare.</li>
      <li>Combining privacy-focused tools (e.g., Tor and Monero/Zcash shielded transactions).</li>
      <li>Browsing and communicating with layered encryption and IP masking.</li>
    </ul>
    </td>
  </tr>
  </tbody>
</table>

<h4>References</h4>
  
  <ol>
    <a href="https://www.whonix.org/wiki/Tips_on_Remaining_Anonymous#Study:_Anonymity_and_Pseudonymity_are_not_the_same" target="_blank"><b>Whonix</b> - Study: Anonymity and Pseudonymity are not the same.</a>
    <a href="https://gitlab.torproject.org/legacy/trac/-/wikis/doc/TorifyHOWTO#ToroverTor" target="_blank">Adrelanos - Do not Mix Anonymity Modes</a>
  </ol>
  
</body>
</html>