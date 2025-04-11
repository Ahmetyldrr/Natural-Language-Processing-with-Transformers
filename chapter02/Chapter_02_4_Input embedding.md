# Giriş Gömmeleri (Input Embedding)

Giriş gömme alt katmanı, giriş tokenlarını orijinal Transformer modelinde öğrenilmiş gömmeler kullanarak $d_{model} = 512$ boyutlu vektörlere dönüştürür: Şekil 2.4: Transformer'ın giriş gömme alt katmanı.

Giriş gömme alt katmanı, diğer standart transdüksiyon modelleri gibi çalışır. Bir tokenlaştırıcı, bir cümleyi tokenlara dönüştürür. Her tokenlaştırıcının Byte-Pair Encoding (BPE), word piece ve sentence piece yöntemleri gibi kendi yöntemleri vardır. Transformer başlangıçta BPE'yi kullanmıştır, ancak diğer modeller diğer yöntemleri kullanır. Hedefler benzerdir ve seçim, seçilen stratejiye bağlıdır.

Örneğin, "The Transformer is an innovative NLP model!" dizisine uygulanan bir tokenlaştırıcı, bir tür modelde aşağıdaki tokenları üretecektir: `['the', 'transform', 'er', 'is', 'an', 'innovative', 'n', 'l', 'p', 'model', '!']`. Bu tokenlaştırıcının dizeyi küçük harfe normalleştirdiğini ve alt parçalara böldüğünü fark edeceksiniz.

Bir tokenlaştırıcı genellikle gömme işlemi için kullanılacak bir tamsayı temsili sağlar. Örneğin:

```python
text = "The cat slept on the couch.It was too tired to get up."
tokenized_text = [1996, 4937, 7771, 2006, 1996, 6411, 1012, 2009, 2001, 2205, 5458, 2000, 2131, 2039, 1012]
```

Bu noktada, tokenleştirilmiş metinde daha ileri gitmek için yeterli bilgi yoktur. Tokenleştirilmiş metin gömülmelidir. Transformer, öğrenilmiş bir gömme alt katmanı içerir. Sonuç olarak, tokenleştirilmiş girdiye birçok gömme yöntemi uygulanabilir.

Ben, Transformer'ın gömme alt katmanını göstermek için 2013 yılında Google tarafından kullanıma sunulan word2vec gömme yaklaşımının skip-gram mimarisini seçtim.

Bir skip-gram, bir pencere içindeki merkez kelimeye odaklanır ve bağlam kelimelerini tahmin eder. Örneğin, eğer `word(i)` iki adımlı bir pencerede merkez kelime ise, bir skip-gram modeli `word(i-2)`, `word(i-1)`, `word(i+1)` ve `word(i+2)`'yi analiz edecektir. Ardından, pencere kaydırılacak ve işlem tekrarlanacaktır.

Bir skip-gram modeli genellikle bir giriş katmanı, ağırlıklar, bir gizli katman ve tokenleştirilmiş giriş kelimelerinin gömme vektörlerini içeren bir çıkış katmanı içerir.

Aşağıdaki cümle için gömme yapmamız gerektiğini varsayalım: "The black brown cat sat on the couch and the dog slept on the rug." İki kelimeye odaklanacağız: "black" ve "brown". Bu iki kelimenin gömme vektörleri benzer olmalıdır.

Her kelime için $d_{model} = 512$ boyutlu bir vektör üreteceğimiz için, her kelime için 512 boyutlu bir gömme vektörü elde edeceğiz.

Örneğin, "black" kelimesinin gömme vektörü:

```python
black = [[-0.01206071, 0.11632373, 0.06206119, 0.01403395, 0.09541149, 0.10695464, 
          0.02560172, 0.00185677, -0.04284821, 0.06146432, 0.09466285, 0.04642421, 
          0.08680347, 0.05684567, -0.00717266, -0.03163519, 0.03292002, -0.11397766, 
          0.01304929, 0.01964396, 0.01902409, 0.02831945, 0.05870414, 0.03390711, 
          -0.06204525, 0.06173197, -0.08613958, -0.04654748, 0.02728105, -0.07830904,
          …,
          0.04340003, -0.13192849, -0.00945092, -0.00835463, -0.06487109, 0.05862355, 
          -0.03407936, -0.00059001, -0.01640179, 0.04123065, -0.04756588, 0.08812257, 
          0.00200338, -0.0931043, -0.03507337, 0.02153351, -0.02621627, -0.02492662, 
          -0.05771535, -0.01164199, -0.03879078, -0.05506947, 0.01693138, -0.04124579, 
          -0.03779858, -0.01950983, -0.05398201, 0.07582296, 0.00038318, -0.04639162, 
          -0.06819214, 0.01366171, 0.01411388, 0.00853774, 0.02183574, -0.03016279, 
          -0.03184025, -0.04273562]]
```

"black" kelimesi şimdi 512 boyutlu bir vektörle temsil ediliyor. Diğer gömme yöntemleri de kullanılabilir ve $d_{model}$ daha yüksek sayıda boyuta sahip olabilir.

"brown" kelimesinin gömme vektörü de 512 boyutludur:

```python
brown = [[1.35794589e-02, -2.18823571e-02, 1.34526128e-02, 6.74355254e-02,
          1.04376070e-01, 1.09921647e-02, -5.46298288e-02, -1.18385479e-02,
          4.41223830e-02, -1.84863899e-02, -6.84073642e-02, 3.21860164e-02,
          4.09143828e-02, -2.74433400e-02, -2.47369967e-02, 7.74542615e-02,
          9.80964210e-03, 2.94299088e-02, 2.93895267e-02, -3.29437815e-02,
          …,
          7.20389187e-02, 1.57317147e-02, -3.10291946e-02, -5.51304631e-02,
          -7.03861639e-02, 7.40829483e-02, 1.04319192e-02, -2.01565702e-03,
          2.43322570e-02, 1.92969330e-02, 2.57341694e-02, -1.13280728e-01,
          8.45847875e-02, 4.90090018e-03, 5.33546880e-02, -2.31553353e-02,
          3.87288055e-05, 3.31782512e-02, -4.00604047e-02, -1.02028981e-01,
          3.49597558e-02, -1.71501152e-02, 3.55573371e-02, -1.77437533e-02,
          -5.94457164e-02, 2.21221056e-02, 9.73121971e-02, -4.90022525e-02]]
```

Bu iki kelime için üretilen gömme vektörlerini doğrulamak için, "black" ve "brown" kelimelerinin gömme vektörlerinin benzer olup olmadığını görmek için kosinüs benzerliğini kullanabiliriz.

Kosinüs benzerliği, birim kürede vektörler oluşturmak için Euclidean (L2) normunu kullanır. Karşılaştırdığımız vektörlerin nokta çarpımı, bu iki vektörün noktaları arasındaki kosinüstür.

Örneğin, "black" ve "brown" vektörleri arasındaki kosinüs benzerliği:

```python
cosine_similarity(black, brown) = [[0.9998901]]
```

Skip-gram, birbirine yakın iki vektör üretti. "black" ve "brown" kelimelerinin bir renk alt kümesini oluşturduğunu tespit etti.

Transformer'ın sonraki katmanları boş elle başlamaz. Bunun yerine, kelimelerin nasıl ilişkilendirilebileceği konusunda zaten bilgi sağlayan öğrenilmiş kelime gömmeleri vardır. Ancak, büyük bir bilgi parçası eksiktir, çünkü bir kelimenin bir dizideki konumunu gösteren ek bir vektör veya bilgi yoktur.

Transformer tasarımcıları başka bir yenilikçi özellik olan konumsal kodlama (positional encoding) ile geldiler. Şimdi, konumsal kodlamanın nasıl çalıştığını görelim.

---

