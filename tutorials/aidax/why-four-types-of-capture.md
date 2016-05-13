[![AIDAX logo](https://raw.githubusercontent.com/astfarias/aidax/master/files/logo/logo2-less.png)](http://aidaxbi.com/)
##Why Four Types of Capture and How Use

os Eventos não podem ser atualizados, é "fire-and-forget"

[8:11] 
e podem ser inseridos diversas vezes

[8:12] 
os atributos são amarrados ao visitante atual, sucessivas gravações sobreescrevem o valor atual

[8:15] 
as transações são semelhantes a eventos, com o diferencial de poderem ser atualizadas , além disso, elas tem um contexto diferente, para facilitar a segmentação(por exemplo, contabilizamos os valores totais de transações como atributo de cliente), também podem ser inseridas quantas vezes quiser

[8:15] 
os objetivos podem ser gravados uma vez por visitante ou uma vez por sessão

[8:16] 
sucessivas gravações sobreescrevem o valor atual

poderíamos ter só eventos? poderíamos, mas aí ficaria nas costas do usuário evitar gravar o mesmo evento várias vezes quando ele na verdade quer um objetivo/meta por visitante/sessão

[8:17] 
no caso das transações é uma especialização de evento que força o dev a gravar status(true, false) e um valor da transação, além de permitir a atualização

[8:17] 
atributos mesma coisa

Exemplo de evento: pageview
ax.track("pageview",{title: "Home"});

Exemplo de atributo: gênero
ax.identify({gender: "M"});

Exemplo de transação:
ax.charge(20, true, { name: "Kit-Kat", $tags: "candy"});

Exemplo de objetivo de visitante: cadastro
ax.goal("subscription", true, true);

Exemplo de objetivo de sessão: enviar formulário
ax.goal("submit_contact_form", true, false);

[8:22] 
é claro, são abstrações e cada um interpreta a melhor maneira de uso. O último exemplo poderia ser um objetivo de visitante ou apenas um evento, depende muito de como o usuário quer mensurar as coisas

tudo está amarrado ao visitante atual

[8:45] 
quer ele seja anônimo ou identificado

[8:46] 
agora, algo interessante

[8:46] 
é que se você está no site como anônimo e de repente se identifica com um email astfarias@foo.com

[8:46] 
todos os seus atributos, eventos, objetivos e transações anônimas migram pro visitante astfarias@foo.com

se você ja estava identificado com um e-mail anterior, apenas os eventos, objetivos e transações da sessão atual são migrados

aliás, não precisa ser um e-mail, pode ser qq coisa que o valha como um RG ou CPF

[8:48] 
o e-mail apenas permite utilizar a automatização de fluxo dos gatilhos

fora as que você captura manualmente, capturamos a geolocalização por IP(imprecisa), a previsão do tempo baseada nas coordenadas geolocalizadas(imprecisa), o dispositivo utilizado para acesso(browser,  ip, idioma, sistema operacional, resolução), parâmetros de campanha(utm) e o referer da sessão

[8:56] 
todas estas informações também disponíveis para segmentação em métricas e perfis  

##References

* [Dust.js doc](http://www.dustjs.com/docs/)
* [Mobify doc](http://adaptivejs.mobify.com/v2.0/docs/)
* [Github user: rek - Gist Dust.js Cheatsheet ](https://gist.github.com/rek/f18a7e38b8e4e3686584)