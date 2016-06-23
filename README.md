Processo de configuração selenium grid

###########################################################################
# Instalar serviço hub                                                    #
###########################################################################

`https://github.com/feniix/selenium-grid-startup`

###########################################################################
# Instalar Cliente                                                        #
###########################################################################

PS.: Garantir que o pacote daemon esteja instalado

## Usuário selenium
`sudo groupadd -r selenium`
`sudo useradd -r -d /var/lib/selenium -s /bin/bash -m -g selenium -G selenium selenium`

## Logs
`sudo mkdir /var/log/selenium`
`sudo chown selenium.selenium /var/log/selenium`

## Baixar jar
`sudo wget --no-check-certificate http://selenium-release.storage.googleapis.com/2.53/selenium-server-standalone-2.53.0.jar -O /var/lib/selenium/selenium-server-standalone-2.53.0.jar`

## Criar link simbolico
`cd /var/lib/selenium
sudo ln -s selenium-server-standalone-2.32.0.jar selenium-server-standalone.jar`

## Arquivos de serviço
`sudo cp /git-repository/config/init.d/selenium /etc/init.d/`
`sudo cp /git-repository/config/default/selenium /etc/default/`

## Permitir execução do script
`sudo chmod +x /etc/init.d/selenium`

## Instalar o serviço
`sudo update-rc.d selenium defaults`

##Iniciar o serviço
`sudo /etc/init.d/selenium start`
ou
`sudo service selenium start`

## Verificar o Log
`sudo tail -f /var/log/selenium/selenium.log`