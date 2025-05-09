## 1. Update Drosera CLI (Droseraup)

```bash
curl -L https://app.drosera.io/install | bash
```
```bash
source /root/.bashrc
```
```bash
droseraup
```

## 2. Update Seed Node in `drosera.roml`
You need to replace the previous Seed Node RPC set in `drosera_rpc` field in `drosera.toml` with new Seed Node.
```bash
cd my-drosera-trap
```
```bash
nano drosera.toml
```
* Replace `https://seed-node.testnet.drosera.io` with new Seed Node: `https://relay.testnet.drosera.io`

![image](https://github.com/user-attachments/assets/589567b1-7b04-4514-af98-f721b29dfde9)


## 3. Verify Trap's Address
In your `drosera.toml` file, Verify that you have a line showing your trap's address as `address = "0x..."`

![image](https://github.com/user-attachments/assets/0db14076-1bbd-40fc-b18d-c785cc94776c)

If you don't see your trap's address as `address = "0x..."` line, then connet your missing trap's wallet to the [Dashboard](https://app.drosera.io/), find it under Trap's Config and Create a line like picture above in `drosera.toml` file.

![image](https://github.com/user-attachments/assets/5f70f788-4a99-4a6b-9f50-4ca5ce99073b)


## 4. Re-Apply Drosera Configurations
```bash
DROSERA_PRIVATE_KEY=xxx drosera apply
```
* Replace `xxx` with your trap's Private Key.
* Enter `ofc`, when prompted.

## 5. Open UDP ports
```console
# 1st operator
ufw allow 31313/udp
ufw allow 31314/udp

# 2nd operator
ufw allow 31315/udp
ufw allow 31316/udp
```


## 6. Re-Run Operator Node(s)
* Head to Operator's directory:
```bash
cd ~
```
```bash
cd Drosera-Network
```

* Stop Nodes:
```bash
docker compose down -v
```

* Restart Nodes:
```bash
docker compose up -d
```

* Node Logs:
```bash
docker compose logs -f
```
* You will get errors initially

![image](https://github.com/user-attachments/assets/c4af432a-cb30-412a-abe4-0e5d0fd5f6ac)

* After a few mintues, you'll get healthy logs:

![image](https://github.com/user-attachments/assets/418229a7-5462-46bd-b81f-a18996a3c822)

Then, Your operators will produce Green Blocks, bro. Congratz.
![image](https://github.com/user-attachments/assets/669b4048-3952-4079-95e1-58dd279e194c)
