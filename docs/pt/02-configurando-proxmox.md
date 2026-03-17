# Configurando o Proxmox

Instalar o Proxmox é bem tranquilo. Se você já instalou alguma distro Linux antes, vai parecer bem parecido, só com alguns passos a mais relacionados a rede e armazenamento.

Já trabalhei com clusters de Proxmox e outros ambientes virtualizados há algum tempo, então nada aqui foi exatamente novidade. Ainda assim, é legal ver como você sai de uma máquina bare-metal para um host de virtualização utilizável com interface web em pouco tempo.

Baixa a ISO, grava, dá boot, next-next-finish e basicamente já está pronto.

## Armazenamento

A parte de armazenamento exigiu um pouco mais de atenção, principalmente por causa da ideia de “usar o que já tem disponível”.

Estou usando uma placa de expansão SATA para ter mais portas, e alguns adaptadores 3D de 5.25" para 2.5" para conseguir acomodar fisicamente todos os discos no gabinete. Nada muito sofisticado, mas resolveu bem sem precisar comprar um gabinete novo.

Os discos são uma mistura de SSDs e HDDs de upgrades anteriores, então não são exatamente uniformes, o que deixa as coisas um pouco mais interessantes.

## ZFS (principalmente)

Decidi usar principalmente ZFS para o armazenamento.

Principais motivos:
- opções de redundância nativas
- snapshots (extremamente úteis em um homelab)
- nunca tinha usado em servidores de produção e já estava na hora

Provavelmente é overkill para alguns cenários, e tem um custo de RAM, mas mesmo com 16GB tem sido tranquilo para o que eu estou fazendo.

Não estou usando ZFS para tudo, mas ele virou a escolha padrão, a menos que eu tenha algum motivo para não usar.

## Pós-instalação

Depois da instalação inicial, tem algumas pequenas coisas que eu gosto de fazer logo de cara.

Primeiro, troquei para o repositório non-subscription. Apesar de isso ser tecnicamente um servidor de produção (eu faço experimentos, mas também rodo alguns serviços privados que vou comentar depois), apontar para o repositório da comunidade e atualizar os pacotes já é suficiente.

Também acabei usando alguns scripts do projeto community-scripts.

- [**PVE Post Install**](https://community-scripts.org/scripts/post-pve-install): faz bastante coisa, mas no meu caso usei só para remover o aviso de subscription. Prefiro manter o sistema mais “limpo” e ir fazendo mudanças de forma intencional, em vez de rodar um script que automatiza tudo.

- [**PVE Cron LXC Updater**](https://community-scripts.org/scripts/cron-update-lxcs): esse adiciona uma tarefa agendada para atualizar todos os containers LXC semanalmente (domingo à meia-noite). É algo simples, mas ajuda a manter tudo razoavelmente atualizado sem precisar pensar muito nisso.

Por enquanto é isso. Prefiro manter as coisas simples no começo e ir automatizando conforme a necessidade aparece.