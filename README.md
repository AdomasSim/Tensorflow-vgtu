# AI Learning Assistant

„AI Learning Assistant“ – tai informacinė sistema, leidžianti įkelti mokymo medžiagą (PDF, DOCX, tekstą) ir naudojant generatyvinį dirbtinį intelektą:

- sugeneruoti dokumento santrauką,
- sugeneruoti testus su pasirinkimų atsakymais ir paaiškinimais,
- sukurti individualų mokymosi planą,
- bendrauti su AI pokalbių režimu apie konkrečią mokomąją medžiagą.

---

## Architektūra

- Backend: **Python (FastAPI)**
- Frontend: **React (TypeScript)**
- DB: **PostgreSQL**
- DI integracija: **LLM API** (pvz., OpenAI)
- UML diagramos: kataloge `uml/` (PlantUML `.puml` failai)

**Pagrindinės UML diagramos:**

- `uml/usecase.puml` – Use Case diagrama
- `uml/components.puml` – komponentų diagrama
- `uml/erd.puml` – ER modelis
- `uml/seq_upload.puml` – dokumento įkėlimas
- `uml/seq_summary.puml` – santraukos generavimas
- `uml/seq_test.puml` – testo generavimas
- `uml/seq_plan.puml` – mokymosi plano generavimas
- `uml/seq_chat.puml` – pokalbio eiga

---

## Duomenų struktūra (`/data/`)

Kataloge `/data/` pateikiami demonstraciniai End-to-End pavyzdžiai, naudojant (X, y) poras:

- `data/example1/`
  - `X.txt` – mokymo medžiagos tekstas
  - `y_summary.txt` – sugeneruota santrauka
  - `y_test.txt` – sugeneruotas testas
  - `y_plan.txt` – sugeneruotas mokymosi planas
  - `y_chat.txt` – pavyzdinis klausimas–atsakymas

Kai įdedamas **X** (įvestis — mokymo medžiagos tekstas), DI turi sugeneruoti keturias skirtingas išvestis (**Y**):

---

### ✅ 1. `y_summary.txt` — santrauka

Tai AI sugeneruota dokumento santrauka:

- glaustas originalaus teksto apibendrinimas,
- 5–7 sakiniai,
- parodo, kad DI supranta dokumento esmę.

**Naudojimas:** pademonstruoja, kad sistema teisingai generuoja santraukas.

---

### ✅ 2. `y_test.txt` — sugeneruotas testas

Tai testas, kurį AI sukuria remdamasis mokymo medžiaga.

Jame būna:

- klausimai,  
- 4 atsakymo variantai,  
- kuris variantas teisingas,  
- teisingo atsakymo paaiškinimas.

**Naudojimas:** parodo, kad AI gali kurti mokymosi vertinimo užduotis iš X turinio.

---

### ✅ 3. `y_plan.txt` — mokymosi planas

Generatyvinis DI sukuria mokymosi planą — kaip studentas turėtų mokytis temą žingsnis po žingsnio:

- paprastai 5 žingsniai,  
- nuo teorijos skaitymo iki praktikos.

**Naudojimas:** demonstruoja personalizuotą mokymosi rekomendacijų generavimą.

---

### ✅ 4. `y_chat.txt` — pavyzdinis klausimas / atsakymas (chat)

Tai trumputė AI pokalbio su studentu simuliacija:

- studentas užduoda klausimą apie X medžiagą,  
- AI atsako remdamasis tekstu.

**Naudojimas:** parodo, kad sistema gali veikti kaip kontekstinis pokalbių botas.
---

## Promptų struktūra (`/prompts/`)

Kataloge `/prompts/` laikomi visi naudojami promptai LLM testavimui ir sistemos generavimui:

- `system_design_prompt.md` – pilnas sistemos projektavimo promptas (šis aprašymas).
- `test_prompt_example1.txt` – promptas, naudojamas generuoti `data/example1/` (X, y) pavyzdžius.
- `test_prompt_example2.txt`
- `test_prompt_example3.txt`

---

## Projekto paleidimas

### Backend (FastAPI)

```bash
cd src/backend
pip install -r requirements.txt
uvicorn main:app --reload
