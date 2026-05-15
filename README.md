# Client-Server Encrypted Communication 

A multi-threaded distributed system built with Python Sockets and the Fernet (Symmetric Encryption) protocol. This project demonstrates secure data retrieval from multiple distributed servers, where numerical data is processed locally, encrypted before transmission, and aggregated at the client side.

---

## System Architecture

The system implements a distributed data processing workflow:
1. **Data Generation:** Random datasets are generated in Excel format to simulate distributed records.
2. **Multi-threaded Servers:** Two local servers run concurrently, each hosting a specific data file.
3. **Encrypted Transmission:** Servers compute a local sum, encrypt it using a shared Fernet key, and send the ciphertext via TCP sockets.
4. **Client Aggregation:** The client connects to both servers, receives the encrypted values, decrypts them using the shared key, and calculates the final global sum.

---

## Security Features
* **Symmetric Encryption:** Uses the `cryptography` library's Fernet implementation (AES-128 in CBC mode).
* **End-to-End Protection:** Data is encrypted at the source (Server) and only decrypted at the destination (Client).
* **Socket Security:** Demonstrates how to prevent raw data exposure during transit across a network.

---

## Technical Stack
* **Language:** Python 3.x
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Core Libraries:**
    * `socket`: For low-level network communication.
    * `cryptography`: For Fernet key management and encryption.
    * `pandas`: For Excel data manipulation.
    * `threading`: For concurrent server and client execution.

---

## Steps 

### 1. Requirements
Ensure you have the following libraries installed:
```bash
pip install pandas cryptography openpyxl
```
### 2. Execution Flow
Since the project is built into a single notebook, follow these steps within `PDCproject.ipynb`:

**1. Data Prep:** Run the first cells to generate file1.xlsx, file2.xlsx, and the fernet_key.key.

**2. Server/Client Logic:** Execute the cells defining start_server and request_sum.

**3. Run Simulation:** Run the final cell. This will:
      * Spawn two background threads representing the distributed servers.
      * Initialize the client task to request, decrypt, and sum the data.

## Results
Upon successful execution, the console will display:

* The connection status of both servers.

* The encrypted ciphertext received by the client.

* The final decrypted global sum.

Note: The fernet_key.key must be present for the client to successfully decrypt server responses. If the key is regenerated, the servers must be restarted to use the updated key.

## Future Enhancements
* **Error Handling:** Adding timeouts for server responses.

* **Network Expansion:** Moving servers to different physical or virtual machines (replacing localhost with actual IP addresses).

* **Asymmetric Exchange:** Using RSA to distribute the shared key securely.

**Developed as part of a Distributed Systems & Cybersecurity Research Project.**
