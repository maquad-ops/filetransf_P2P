================================================================================
          P2P ENCRYPTED FILE TRANSFER - README
================================================================================

A secure, peer-to-peer file transfer application that runs entirely in your
browser. No server setup, no file uploads to the cloud – just a direct,
encrypted connection between two peers.


================================================================================
1. FEATURES
================================================================================

  * End-to-end encryption – Files are encrypted with AES-GCM using a shared key.
  * Simple pairing – A single Base64 code combines the peer ID and the key.
  * No registration – Uses PeerJS for WebRTC signalling.
  * Standalone HTML – Open the file in any modern browser; nothing else to install.
  * Real-time status – Visual feedback for connection and file transfer progress.


================================================================================
2. HOW IT WORKS
================================================================================

  1. Each peer opens the HTML page and generates a unique shareable code.
  2. The code contains:
       - The peer's unique ID (used to establish the WebRTC connection)
       - A random 256-bit key (used for AES-GCM encryption)
  3. Peers exchange codes (e.g. via chat, email, or QR).
  4. One peer pastes the other's code and clicks Connect.
  5. Once connected, either peer can select a file and click Send File.
  6. The file is encrypted with the shared key, transmitted directly, and
     decrypted on the receiver's side.
  7. The receiver's browser automatically downloads the decrypted file.


================================================================================
3. GETTING STARTED
================================================================================

  Prerequisites
  -------------
  A modern web browser (Chrome, Firefox, Edge, Safari) with WebRTC support.
  Internet access (for the PeerJS signalling server).

  Installation
  ------------
  No installation is required. Just download the single HTML file and open it
  in your browser.

    # Clone or download the repository
    git clone https://github.com/yourusername/p2p-encrypted-file-transfer.git
    cd filetransf_P2P

  Open index.html in your browser.


================================================================================
4. USAGE GUIDE
================================================================================

  Step 1 – Generate your code
  ---------------------------
  - When the page loads, your peer ID is generated automatically.
  - Click the "Genera nuovo codice" button (or wait for it to auto-generate).
  - Your shareable code appears in the grey box.

  NOTE: This code is unique per session. Regenerate it if you need a new key.

  Step 2 – Share your code
  ------------------------
  - Copy the code using the "Copia" button.
  - Send it to the other peer via any secure channel (e.g. encrypted message).

  Step 3 – Connect to the remote peer
  -----------------------------------
  - The other peer should also open the page and generate their own code.
  - In your page, paste their code into the input field under
    "Connetti al peer remoto".
  - Click "Connetti".

  IMPORTANT: Both peers must be online and reachable. The connection uses
  WebRTC, so NAT/firewall traversal is handled by PeerJS.

  Step 4 – Transfer files
  -----------------------
  - Once connected, the status badge turns green ("Connesso!").
  - Select a file using the file picker.
  - Click "Invia file".
  - The file is encrypted and sent.
  - The receiving peer will automatically download the decrypted file.


================================================================================
5. SECURITY CONSIDERATIONS
================================================================================

  * Encryption – AES-GCM with a 256-bit key (generated via crypto.getRandomValues).
  * Key exchange – The shared key is embedded in the shareable code. DO NOT
    transmit this code over an insecure channel; use a secure side-channel
    (e.g. Signal, WhatsApp, or in-person).
  * WebRTC – The data channel is encrypted by default, but the additional
    application-layer encryption adds defence-in-depth.
  * No logging – No data is stored or logged on any server; the signalling
    server only helps peers find each other.


================================================================================
6. DEPENDENCIES
================================================================================

  * PeerJS – WebRTC signalling and connection management (loaded from CDN).
  * Web Crypto API – Built-in browser cryptography.

  All other code is vanilla HTML/CSS/JavaScript.


================================================================================
7. LIMITATIONS
================================================================================

  * Maximum file size is limited by browser memory (typically a few hundred MB).
  * Both peers must be online simultaneously for the transfer.
  * Relies on the public PeerJS signalling server (0.peerjs.com). For production,
    consider hosting your own signalling server.
  * No chunked uploads – the entire file is read into memory before sending.


================================================================================
8. CONTRIBUTING & LICENSE
================================================================================

  Contributing
  ------------
  Contributions are welcome! Please open an issue or submit a pull request.

  License
  -------
  This project is licensed under the MIT License – see the LICENSE file for
  details.

  Contact
  -------
  For questions or feedback, please open an issue on GitHub.


================================================================================
Enjoy secure, direct file sharing!
================================================================================