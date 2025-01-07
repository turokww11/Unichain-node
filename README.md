# Unichain-node
Uniswap — является крупнейшей автоматизированной маркет-мейкерской площадкой (AMM) DEX на виртуальной машине Ethereum

Инвестировали: $188 000 000
Инвесторы: Paradigm, a16z, Polychain, Coinbase и другие
Характеристики: 6CPU/16RAM/400SSD — рекомендованные / 4CPU/8RAM/60SSD — минимальные
Многие уже знают, недавно, Uniswap запустили запуск своего Layer2, под названием — Unichain, я кстати даже гайд сделал по тестовой сети

Дополнительно к тестовой активности, можно установить ноду от Unichain, при этом сделать все возможные активности в данном чейне
Устанавливаем ноду. Детальный гайд
Устанавливаем MobaXterm
Подключаемся на арендованный сервер через root
Выполняем команды по списку:

.Обновляем и устанавливаем необходимые пакеты

sudo apt update && sudo apt upgrade -y

.Устанавливаем докер

sudo apt install docker.io

.Устанавливаем Docker compose

sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

.Клонируем репозиторию Unichain

git clone https://github.com/Uniswap/unichain-node

.Меняем директорию на unichain-node

cd unichain-node

.Открываем нано конфиг .env.sepolia

nano .env.sepolia

.Заменяем RPC

OP_NODE_L1_ETH_RPC=https://ethereum-sepolia-rpc.publicnode.com
OP_NODE_L1_BEACON=https://ethereum-sepolia-beacon-api.publicnode.com

.Сохраняем содержимое Cntr + X, Y, Enter

.Запускаем ноду

docker-compose up -d

.Пробуем curl нашу ноду

curl -d '{"id":1,"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false]}' \
  -H "Content-Type: application/json" http://localhost:8545

  .Проверяем логи unichain-node-op-node-1

  docker logs unichain-node-op-node-1

  .Проверяем логи unichain-node-execution-client-1

  docker logs unichain-node-execution-client-1

  
