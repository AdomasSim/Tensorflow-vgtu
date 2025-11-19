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

Analogiškai:  
- `data/example2/`  
- `data/example3/`

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
