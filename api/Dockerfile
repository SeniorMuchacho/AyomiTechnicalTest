FROM python:3.12

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -r requirements.txt


RUN apt-get update && apt-get install -y sqlite3

COPY script_db.py /app/script.py

RUN sqlite3 /app/expressions.db \
    "CREATE TABLE expressions (id INTEGER PRIMARY KEY, expression TEXT, result REAL);"

CMD ["python", "/app/script.py"]

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]