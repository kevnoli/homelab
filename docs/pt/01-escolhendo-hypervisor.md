# Começando o homelab: escolhendo um hypervisor

Quando comecei a montar meu homelab, a primeira decisão de verdade foi como eu queria rodar os serviços no servidor.

Existiam algumas opções:

- Simplesmente instalar uma distro Linux (como Debian ou Ubuntu) e rodar tudo diretamente nela usando Docker.

- Usar algo como [TrueNAS](https://www.truenas.com/truenas-community-edition/) ou [Unraid](https://unraid.net/) e rodar os aplicativos por meio dessas plataformas.

- Utilizar um hypervisor para dividir os serviços entre máquinas virtuais e containers.

A primeira opção com certeza funcionaria e, honestamente, é a mais simples. Mas eu sabia que, conforme o homelab fosse crescendo, isolar os serviços seria útil. Poder subir uma VM, quebrar alguma coisa e simplesmente voltar atrás é algo bem valioso quando você está experimentando.

Foi isso que me levou a usar um hypervisor. Acabei escolhendo o [Proxmox Virtual Environment](https://www.proxmox.com/en/), que é open source e permite gerenciar tanto VMs completas (KVM) quanto containers leves (LXC) através de uma interface web.

Eu poderia ter feito tudo manualmente em um Linux “puro”? Claro. Na prática, é basicamente isso que o Proxmox faz por baixo dos panos. Mas a camada de gerenciamento e as ferramentas acabam economizando bastante tempo.

# O servidor em si

O hardware é meio que um Frankenstein, montado principalmente com peças que fui acumulando ao longo dos anos.

O hardware principal dele é:
- Xeon E5-2630L v3  
- 16GB de RAM ECC  
- placa-mãe Machinist MR9A  

Os três vieram do AliExpress.

O resto é ainda mais improvisado:

- a GPU GTX 1050 e o gabinete foram comprados usados  
- a fonte era a que alimentava meu PC principal antes de eu fazer um upgrade  
- os discos são uma mistura de SSDs e HDDs que foram sobrando de upgrades em outras máquinas  

Definitivamente não é um servidor de rack bonito, mas é exatamente aí que está a graça.

# Facilitando as coisas

Mesmo sendo possível configurar tudo manualmente dentro do Proxmox e dos containers, eu rapidamente descobri os [scripts do tteck](https://community-scripts.org/)([Github](https://github.com/community-scripts/ProxmoxVE)).

Além de scripts para instalar rapidamente vários serviços comuns, eles também fornecem alguns scripts de gerenciamento bem úteis, que cuidam de coisas como atualizações, limpeza de kernels antigos e outras pequenas tarefas de manutenção. Eles são muito práticos e me economizaram bastante tempo enquanto eu montava o servidor.

Infelizmente o criador, tteck, faleceu no ano passado, o que foi uma grande perda para a comunidade. Mesmo assim, o trabalho dele continua no repositório e ainda ajuda muita gente que está começando.

Então, apesar de eu ainda gostar de instalar e definir as configurações na mão, confesso que para muitos serviços eu simplesmente rodo um desses scripts e sigo em frente.