# Gemini CLI

Script interattivo per chattare con Google Gemini direttamente dal terminale.

## Requisiti

- Python 3.14 (installato via Homebrew)
- Virtualenv dedicato in `~/.venvs/gemini`
- Package `google-genai`

## Ambiente virtuale

Il progetto usa un ambiente virtuale Python isolato per evitare conflitti con il sistema.

**Creazione venv (già fatto):**

```bash
/opt/homebrew/bin/python3 -m venv ~/.venvs/gemini
~/.venvs/gemini/bin/pip install google-genai
```

**Aggiornamento dipendenze in futuro:**

```bash
~/.venvs/gemini/bin/pip install --upgrade google-genai
```

## Script

Il file `~/bin/gemini` usa il shebang puntato al Python del virtualenv:

```
#!/Users/fabrizio/.venvs/gemini/bin/python3
```

## Configurazione

### Chiave API

Esporta la variabile d'ambiente `GOOGLE_API_KEY` nel tuo shell config (`~/.zshrc`):

```zsh
export GOOGLE_API_KEY='la_tua_chiave_api'
```

Ottieni la chiave da [Google AI Studio](https://aistudio.google.com).

### Modello

Di default usa `gemini-2.5-flash`. Puoi cambiarlo con la variabile `GEMINI_MODEL`:

```zsh
export GEMINI_MODEL='gemini-2.5-pro'
```

## Utilizzo

```bash
gemini
```

Digita `exit`, `quit` o `esci` per chiudere la sessione.

Puoi anche usare pipe:

```bash
echo "Qual è la capitale dell'Italia?" | gemini
```

## Aggiornamento di Python

Se in futuro vuoi aggiornare Python all'ultima versione stabile:

1. Aggiorna Homebrew e Python:
   ```bash
   brew update && brew upgrade python
   ```

2. Ricrea il virtualenv con il nuovo Python:
   ```bash
   rm -rf ~/.venvs/gemini
   /opt/homebrew/bin/python3 -m venv ~/.venvs/gemini
   ~/.venvs/gemini/bin/pip install google-genai
   ```

3. Aggiorna il shebang in `~/bin/gemini` se il percorso di Python cambia.

## Cronologia aggiornamenti

- **2026-05-13**: Passaggio da Python 3.9 di sistema a Python 3.14 via Homebrew + virtualenv dedicato. Risolti warning EOL di `google-auth` e `urllib3`.
