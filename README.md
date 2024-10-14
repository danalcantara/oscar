E o oscar vai para...
1- Quantas vezes Natalie Portman foi indicada ao Oscar?
Natalie Portman foi indicada 3 vezes ao Oscar.

db.goesTo.find({entity: 'Natalie Portman'});



2- Quantos Oscars Natalie Portman ganhou?
Natalie Portman ganhou 1 Oscar.

db.goesTo.countDocuments({nome_do_indicado: "Natalie Portman", vencedor: "true"})



3- Amy Adams já ganhou algum Oscar?
Amy Adams não ganhou nenhum Oscar.

db.goesTo.countDocuments({nome_do_indicado: "Amy Adams", vencedor: "true"})



4- A série de filmes Toy Story ganhou um Oscar em quais anos?
Toy Story 3 ganhou o Oscar 2 vezes

db.goesTo.find({entity:"Toy Story"});
db.goesTo.find({entity:"Toy Story 2"});
db.goesTo.find({entity:"Toy Story 3", winner: true});



5- A partir de que ano a categoria "Actress" deixa de existir?
Acredito que essa categoria nunca deixou de existir, só mudou de nome durante os séculos

db.goesTo.find({category:"ACTRESS"});
db.goesTo.countDocuments({category:"ACTRESS"});



6- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
Foi para Janet Gaynor, em 1927.

db.goesTo.find({category: "ACTRESS", year:1927});



7- No campo "Vencedor", altere todos os valores "true" para 1 e todos os valores "false" para 0.
db.goesTo.updateMany({winner:true}, {$set: {winner:1}});
  {
  acknowledged: true,
  insertedId: null,
  matchedCount: 3217,
  modifiedCount: 3217,
  upsertedCount: 0
}

db.goesTo.updateMany({winner: "false"}, {$set: {winner: "0"}})
  {
  acknowledged: true,
  insertedId: null,
  matchedCount: 7841,
  modifiedCount: 7841,
  upsertedCount: 0
}



8- Em qual edição do Oscar "Crash" concorreu ao Oscar?
2006

db.goesTo.find({entity:"Crash"});



9- Dê um Oscar para um filme que merece muito, mas não ganhou.
E o oscar vai para... 13 Indo 30

db.goesTo.insertOne({"_id": ObjectId, "category":'DIRECTING (Dramatic Picture)DIRECTING (Dramatic Picture)', "entity": '13 Going 30', "winner":1});



10- O filme "Central do Brasil" aparece no Oscar?
Sim, aparece como "Central Station"

db.goesTo.find({entity:"Central Station"});



11- Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que merecem ser.
  db.goesTo.insertMany([
    {
        "_id": ObjectId,
        "category": 'DIRECTING (Dramatic Picture)',
        "entity": 'Deadpool & Wolverine',
        "winner": 1,
        "year": 2024
    } ,
    {
        "_id": ObjectId,
        "category": 'DIRECTING (Dramatic Picture)',
        "entity": 'StepUp 3',
        "winner": 1,
        "year": 2014
    } ,
    {
        "_id": ObjectId,
        "category": 'DIRECTING (Dramatic Picture)',
        "entity": 'The Emperors New Groove',
        "winner": 1,
        "year": 2000
    }
]);



12- Pensando no ano em que você nasceu: Qual foi o Oscar de Melhor Filme, Melhor Atriz e Melhor Diretor?
Melhor Filme: Ray

Melhor Atriz: Hilary Swank

Melhor Diretor: Million Dolllar Baby

Melhor Filme:
{year:2004, winner:1, category:"BEST PICTURE"}
Melhor Atriz:
{year:2004, category:"ACTRESS IN A LEADING ROLE", winner:1}
Melhor Diretor:
{year:2004, category:"DIRECTING"}
