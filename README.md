readme: ⚠️ This repository has moved to https://github.com/Knukie/Vichat-monorepo
  # @valki/contracts — Shared TypeScript Contracts for Vichat

  `@valki/contracts` is het officiële domeinmodel- en typepakket voor het **Vichat** platform.  
  Zowel de Vichat Backend (voorheen intern “valki-bot”) als de Vichat Widget (theme: *Valki Talki*) gebruiken dit package om **één gedeelde bron van waarheid** te hebben voor alle conversatie- en chattypes.

  Door deze contracts te gebruiken blijven frontend & backend volledig synchroon, zonder datatypes die langzaam uit elkaar drijven.

  ---

  ## 🎯 Doel van dit package

  - Eén centrale plek voor alle Vichat domeintypes
  - FE/BE synchronisatie zonder duplicate code
  - Veiligere API-communicatie door sterke TypeScript-types
  - Vervanging van losse ad-hoc interfaces binnen de projectcode
  - Basis voor toekomstige Zod validators + OpenAPI generaties

  Dit package bevat **alle datamodellen die Vichat gebruikt** in het hele platform.

  ---

  ## 📦 Inhoud van het contract-pakket

  Momenteel bevat `@valki/contracts` de volgende types (en enums):

  ### 🟨 Message
  - id  
  - conversationId  
  - role (assistant / user / system / agent)  
  - content  
  - images: ImageMeta[]  
  - timestamps  

  ### 🟧 Conversation
  - id  
  - userId  
  - agentId (optioneel)  
  - status (open/closed/pending)  
  - lastMessage  
  - timestamps  

  ### 🟦 User
  - id  
  - role  
  - isBanned  
  - locale  
  - timestamps  

  ### 🟪 ImageMeta
  - url  
  - width  
  - height  
  - mime  
  - size  
  - uploadedAt  

  ### Enums
  - `Role`
  - `UserRole`
  - `UserStatus`
  - `ConversationStatus`

  ---

  ## 🧱 Projectstructuur



valki-contracts/
├── src/
│ ├── message.ts
│ ├── user.ts
│ ├── conversation.ts
│ ├── image.ts
│ └── index.ts
├── dist/
├── tsconfig.json
└── package.json


Alle exports worden centraal opnieuw geëxporteerd vanuit `src/index.ts`.

---

## 🚀 Installatie (voor Vichat Backend & Widget)

Gebruik altijd de main-branch:

```sh
npm install https://github.com/Knukie/valki-contracts.git#main


Of in package.json:

{
  "dependencies": {
    "@valki/contracts": "github:Knukie/valki-contracts#main"
  }
}

🧩 Gebruik in Vichat projecten
In de Vichat Backend (valki-bot):
import type { Message, Conversation } from "@valki/contracts";

In de Vichat Widget (theme: Valki Talki):
import type { Message, ImageMeta } from "@valki/contracts";


De types zijn volledig FE/BE compatible.

🔨 Build
npm run build


Dit genereert de dist/ map in ES module formaat.

📡 Roadmap voor het contract-pakket
1. Zod runtime validators

Automatisch valideren van inkomende API payloads

Bijv. MessageSchema.parse(req.body)

2. OpenAPI / Swagger generator

Contract → automatisch API documentatie

Contract → automatisch client SDK’s

3. Versiebeheer & changelog (semver)

Contract-wijzigingen documenteren

Automatische “breaking change” detectie

4. Splitten in server/client varianten

@vichat/contracts-server

@vichat/contracts-client

5. JSON schema export

Voor validatie in frontend forms en edge environments

🎨 Branding

Platform / productnaam: Vichat

Frontend theme: Valki Talki (selecteerbaar als theme)

Technische package-naam: @valki/contracts
→ mag blijven zoals het is (industry best practice: interne technische naam ≠ merknaam)

📝 Licentie

Private project — alle rechten voorbehouden.
Niet bedoeld voor publieke distributie zonder toestemming.
