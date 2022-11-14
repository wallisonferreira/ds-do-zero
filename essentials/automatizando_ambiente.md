# Aula 25

## FROM
## RUN/CMD
## LABEL
## EXPOSE 80/tcp
## docker run -p 80:80 <host:container>
## ENV <key>=<value>

# Instruções COPY

## COPY [--chown=<user>:<group>] <src>...<dest>
## ADD hom* /mydir/
## ADD test.txt relativeDir/
### Caminho relativo é o WORKDIR no container ex: ./tmp

# Instrução ENTRYPOINT (pós-build do container)

## ENTRYPOINT ["executable","param1","param2"]

FROM debian:stable
RUN apt-get update && apt-get install -y --force-yes apache2
EXPOSE 80 443
ENTRYPOINT ["/usr/sbin/apache2ctl","-D","FOREGROUND"]

# Instrução WORKDIR

## WORKDIR /path/to/workdir
## WORKDIR /dir1
## WORKDIR dir2
## WORKDIR dir3
