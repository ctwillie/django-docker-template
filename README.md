## Setup Instructions

1. Create and activate a virtual environment in the root of the project
```sh
python -m virtualenv venv
source venv/bin/activate
```

2. Install dependencies
```sh
pip install -r requirements.txt
```

3. Run `cp .env.example .env`

4. Generate a secret to populate `DJANGO_SECRET_KEY` in .env
```sh
# generate a secret from the command line
python -c "import secrets; print(secrets.token_hex())"
```

5. Run the docker containers: `docker compose up`

6. Run the database migrations in the `web` container
```sh
docker compose exec web sh
# inside the container
python manage.py migrate
```

7. Create a super user
```sh
docker compose exec web sh
# inside the container
python manage.py createsuperuser
```

8. Navigate to localhost:8000