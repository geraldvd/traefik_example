# Run Docker Backend without anything else

`docker build -t backend ./backend`
`docker run -it -p 8000:80 backend uvicorn main:app --host 0.0.0.0 --port 80`
