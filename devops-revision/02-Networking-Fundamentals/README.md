# 🌐 Module 02: Networking for DevOps (Hinglish Edition)

Bhai, DevOps mein server kaise baat karte hain? Networking hi woh "Road" hai jispe sara traffic chalta hai. 

## 🛰️ The OSI Model (ELI5)
**Analogy**: Socho aapne Amazon se ek phone order kiya.
1. **Physical**: Delivery boy bike pe aa raha hai (Cables/Wi-Fi).
2. **Network**: Packaging pe aapka Pincode hai (IP Address).
3. **Transport**: Packet sahi se pahuncha ya nahi check karna (TCP/UDP).
4. **Application**: Aapne phone khola aur Amazon app use kiya (HTTP/DNS).

### 🔑 Key Concepts (Interview Ready)
- [ ] **DNS (Domain Name System)**: Yeh "Phonebook" hai internet ki. `google.com` ko IP address `142.250.x.x` mein convert karta hai. Netflix ke cloud servers isi base pe connected hain.
- [ ] **VPC (Virtual Private Cloud)**: Aapka private network cloud mein. GCP mein hum ise "Network isolation" ke liye use karte hain.
- [ ] **Load Balancing**: Socho **Zomato** pe ek sath 10,000 orders aa gaye. Ek server hang ho jayega. Load Balancer kya karta hai? Woh traffic ko 10 servers mein divide kar deta hai automatically!

---

## 🛠️ Essential Commands (Cheat Sheet)
- `ping google.com`: Check karo net chal raha hai ya nahi basic level pe.
- `dig google.com` or `nslookup`: Domain resolve ho raha hai ya nahi. (Dhyan rakho, interview mein ye pucha jata hai!)
- `netstat -tulnp`: Kaunse applications ports pe "Listen" kar rahe hain? 
- `curl -v http://example.com`: Detail mein dekhne ke liye ki Request kya ja rahi hai aur Response kya aa raha hai.

---

## ❓ Interview Questions (Smart Jawab)
> [!IMPORTANT]
> **Q1: TCP aur UDP mein antar kya hai?**
> *A: TCP (Transmission Control Protocol) reliable hai. Jab file download karni ho toh TCP zaroori hai taaki ek bhi byte miss na ho (Three-way handshake hota hai). UDP fast hai par thoda data leak ho sakta hai. Video calls ya gaming mein UDP best hai.*

> [!TIP]
> **Q2: Subnetting kya hoti hai?**
> *A: Bade network ko chhote pieces mein divide karna. Jaise ek poori company ke network ko department-wise divide kar dena (Dev, HR, Sales).*

---

## 📚 Resources
- [Networking for Beginners (YouTube)](https://www.youtube.com/watch?v=S7EZueX_p8Y)
- [Cloudflare: What is Networking?](https://www.cloudflare.com/learning/network-layer/what-is-networking/)
