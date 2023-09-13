FROM python:3.8.18 as base

FROM base as builder

RUN apt-get -qq update
RUN apt-get install -y g++

COPY requirements.txt .

RUN pip install --upgrade pip
RUN pip install --prefix="/install" -r requirements.txt

FROM base
COPY --from=builder /install /usr/local

COPY . .
RUN chmod +x ./loadgen.sh
RUN apt-get -qq update
RUN apt-get install -y curl
ENTRYPOINT ./loadgen.sh
