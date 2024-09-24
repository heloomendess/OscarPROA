<h1>E o oscar vai para...</h1>

<h3>Exercícios</h3>

<h4>1- Quantas vezes Natalie Portman foi indicada ao Oscar?</h4>
<p>Natalie Portman foi indicada 3 vezes ao Oscar.</p>

<pre>db.goesTo.find({entity: 'Natalie Portman'});</pre>

<br><br>

<h4>2- Quantos Oscars Natalie Portman ganhou?</h4>
<p>Natalie Portman ganhou 1 Oscar.</p>

<pre>db.goesTo.countDocuments({nome_do_indicado: "Natalie Portman", vencedor: "true"})</pre>

<br><br>

<h4>3- Amy Adams já ganhou algum Oscar?</h4>
<p>Amy Adams não ganhou nenhum Oscar.</p>

<pre>db.goesTo.countDocuments({nome_do_indicado: "Amy Adams", vencedor: "true"})</pre>

<br><br>

<h4>4- A série de filmes Toy Story ganhou um Oscar em quais anos?</h4>
<p>Toy Story 3 ganhou o Oscar 2 vezes</p>

<pre>db.goesTo.find({entity:"Toy Story"});</pre>
<pre>db.goesTo.find({entity:"Toy Story 2"});</pre>
<pre>db.goesTo.find({entity:"Toy Story 3", winner: true});</pre>

<br><br>

<h4>5- A partir de que ano a categoria "Actress" deixa de existir?</h4>
<p>Acredito que essa categoria nunca deixou de existir, só mudou de nome durante os seculos</p>

<pre>db.goesTo.find({category:"ACTRESS"});</pre>
<pre>db.goesTo.countDocuments({category:"ACTRESS"});</pre>

<br><br>

<h4>6- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?</h4>
<p>Foi para Janet Gaynor, em 1927.</p>

<pre>db.goesTo.find({category: "ACTRESS", year:1927});</pre>

<br><br>

<h4>7- No campo "Vencedor", altere todos os valores "true" para 1 e todos os valores "false" para 0.</h4>

<pre>db.goesTo.updateMany({winner:true}, {$set: {winner:1}});</pre>
<pre>
  {
  acknowledged: true,
  insertedId: null,
  matchedCount: 3217,
  modifiedCount: 3217,
  upsertedCount: 0
}
</pre>
<br>

<pre>db.goesTo.updateMany({winner: "false"}, {$set: {winner: "0"}})</pre>
<pre>
  {
  acknowledged: true,
  insertedId: null,
  matchedCount: 7841,
  modifiedCount: 7841,
  upsertedCount: 0
}
</pre>

<br><br>

<h4>8- Em qual edição do Oscar "Crash" concorreu ao Oscar?</h4>
<p>2006</p>

<pre>db.goesTo.find({entity:"Crash"});</pre>

<br><br>

<h4>9- Dê um Oscar para um filme que merece muito, mas não ganhou.</h4>
<p>E o oscar vai para... 13 Going 30</p>

<pre>db.goesTo.insertOne({"_id": ObjectId, "category":'DIRECTING (Dramatic Picture)DIRECTING (Dramatic Picture)', "entity": '13 Going 30', "winner":1});</pre>

<br><br>

<h4>10- O filme "Central do Brasil" aparece no Oscar?</h4>
<p>Sim, aparece como "Central Station"</p>

<pre>db.goesTo.find({entity:"Central Station"});</pre>

<br><br>

<h4>11- Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que merecem ser.</h4>

<pre>
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
</pre>

<br><br>

<h4>12- Pensando no ano em que você nasceu: Qual foi o Oscar de Melhor Filme, Melhor Atriz e Melhor Diretor?</h4>
<p>Melhor Filme: Ray</p>
<p>Melhor Atriz: Hilary Swank</p>
<p>Melhor Diretor: Million Dolllar Baby </p>

<h4>Best Picture:</h4>
<pre>{year:2004, winner:1, category:"BEST PICTURE"}</pre>

<h4>Melhor Atriz:</h4>
<pre>{year:2004, category:"ACTRESS IN A LEADING ROLE", winner:1}</pre>

<h4>Melhor Diretor:</h4>
<pre>{year:2004, category:"DIRECTING"}</pre>
