Scenario framing: "Reconstructed a five-stage OAuth consent-phishing kill chain in a live Azure tenant through forensic analysis of two linked app registrations."




 1. ENTRY. A user was phished. This user was the owner of an App "Mad-Hat-Legacy-Sync-Service"
 - I begun my investigation by opening the "App registrations"
 - The Incident team has left a note in the Internal notes section located in Branding & Properties as part of their investigation.

<img width="1334" height="805" alt="image" src="https://github.com/user-attachments/assets/7aa6f858-b63d-4796-86e3-088642af903a" />


 ESCALATE. The attacker has created a client secret, elevating their user access. The expiry date shows that the attacker has permanently removed the need to sign-in normally.
<img width="1340" height="635" alt="image" src="https://github.com/user-attachments/assets/5fa8cc52-fccc-490a-aa44-c455dd5dc658" />
We can see in the screenshot below that the app can read all directory data and read all users profiles.

<img width="1817" height="685" alt="image" src="https://github.com/user-attachments/assets/36e8c5b9-7844-4291-93d2-1e6b0941efcf" />


 PIVOT. To maintain access (not reliant on the secret), the attacker listed their app as the owner to the legacy app.
 The screenshot below shows the owner of this app. Since they are listed as the owner, they can view and edit this application registration.

<img width="1439" height="649" alt="image" src="https://github.com/user-attachments/assets/90e4dee3-6025-4e6e-8b11-d15f05803540" />

Investigating Mad-Hat-Labs-App
<img width="1376" height="796" alt="image" src="https://github.com/user-attachments/assets/cac7922f-6eef-4c35-a046-23e2e533151e" />



 PERSIST. The attacker implemented a scope that allows the attackers app to request delegated access.

<img width="1445" height="784" alt="image" src="https://github.com/user-attachments/assets/29b59b6e-3857-4a91-83fc-1f720c3c70e2" />


 LOOT. a redirect URI on the rogue app pointing at attacker-controlled infrastructure. Since I was already signed in, I consented to the rogue-app to use my credentials.
 <img width="840" height="665" alt="image" src="https://github.com/user-attachments/assets/f5096663-2087-4264-8cea-9155cd36d566" />

What surprised me
- How a simple mistake (accidentally giving a user owner privileges) can quickly escalate to a damaging and persistent attack if that user's credentials is ever compromised.

Findings and recommendations
- We were able to find the rogue app, and the vulnerabilities of the legacy app.
- It is recommended that:
  1. All users are only given their necessary permissions and access.
  2. Legacy apps are monitored and decommissioned if necessary.
  3. Routine auditing of users permissions and ownership.

What I learned
- I learnt how attackers can make login credentials persistent
- I learnt how attacks can use redirect URIs to phish for credentials
- I learnt how to investigate and trace a phishing attack.
