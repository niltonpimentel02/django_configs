# <project>

[![Python application](https://github.com/niltonpimentel02/nilton_pimentel/actions/workflows/main.yml/badge.svg)](https://github.com/niltonpimentel02/<project>/actions/workflows/main.yml)

## Aplicação disponível em:

https://<project>.herokuapp.com/

## Como desenvolver?

1. Clone o repositório.
2. Crie um virtualenv com Python 3.9.0
3. Ative o virtualenv.
4. Instale as dependências.
5. Configure a instância com o .env.
6. Execute os testes.

```console
git clone git@github.com:niltonpimentel02/<project>.git <project>
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp contrib/env-sample .env
pytest
```

## Como fazer o deploy no heroku?

1. Crie uma instância no heroku.
2. Envie as configurações para o heroku.
3. Define um SECRET_KEY segura para instância.
4. Defina DEBUG=False.
5. Configure o serviço de email.
6. Envie o código para o heroku.

```console
heroku create <project>

heroku config:set SECRET_KEY=`python contrib/secret_gen.py`
heroku config:set DEBUG=False
heroku config:set ALLOWED_HOSTS=.herokuapp.com
heroku config:set EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend
heroku config:set EMAIL_HOST=smtp.sendgrid.com
heroku config:set EMAIL_PORT=587
heroku config:set EMAIL_USE_TLS=True
heroku config:set EMAIL_HOST_USER=apikey
heroku config:set EMAIL_HOST_PASSWORD=<password>
heroku config:set DEFAULT_FROM_EMAIL=name@example.com
heroku config:set SERVER_EMAIL=

git push heroku main --force
```
