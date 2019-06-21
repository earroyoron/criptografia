# Criptografía

---

## Principios básicos

El tratamiento de la información ha requerido desde antiguo garantizar determinadas propiedades:
- Saber el origen de la información: autenticidad y no repudio.
- Estar seguros de que no fue modificada: integridad.
- Proteger el acceso a la información: confidencialidad 
- Asegurar el momento en que tuvo lugar: existencia.

---

Estos requisitos han estado siempre presentes, desde la más remota antigüedad en contratos, planes militares, patentes e inventos,… y se resolvían por diferentes medios:
- Se lacraban o cifraban los mensajes y documentos para garantizar su confidencialidad.
- Se emitían sellos y firmas para demostrar su autenticidad y no repudio.
- Se usaban notarios públicos, para demostrar el momento y añadir una Tercera Parte Confiable.

---

La criptografía (del griego κρύπτω krypto, «oculto», y γράφω graphos, «escribir», literalmente «escritura oculta») es el arte o ciencia de cifrar y descifrar información mediante técnicas especiales.
The reversible transformation of data from the original (the plaintext) to a difficult-to-interpret 

---

La criptografía está fundada en la matemática discreta, la teoría de los números, teoría de la información, estadística y probabilidades,…
Una aproximación histórica a la criptografía permite distinguir tres grandes eras:
La criptografía clásica o antigua: desde la antigüedad hasta la invención de las primeras máquinas de cifrado (Lorenz, Enigma, Purple,…) en las primeras décadas del S.XX.
Una etapa intermedia con la criptografía mediante máquinas de cifrado y un importante desarrollo teórico (Shannon, Teoría de la Información,…) 
La criptografía moderna, con la invención del algoritmo Lucifer (precursor de BES) a mediados de los años 70, la criptografía asimétrica (Diffie-Hellman) en 1976 y el algoritmo RSA en 1978

---

La diferencia entre cifrar y encriptar

---

Son algoritmos que transforman un contenido de longitud variable en un valor de longitud fija, pero que en el caso de los resúmenes criptográficos aportan las siguientes propiedades:
Si  h = hash(x)
El tamaño de h es siempre el mismo.
El cálculo de hash(x) es rápido
No es posible conocer o calcular x a partir de h
Dado h es complejo encontrar otro h’ tal que h=h’ (colisión)

---

Realiza el proceso de cifrado convirtiendo el texto plano en texto cifrado bit a bit.
Utilizan claves de tamano pequeño (128 bits).
La transformación sobre los bits varía.
RC4 es uno de los cifrados por flujo más utilizado.
Se utiliza en aplicaciones donde la longitud del texto plano no es conocida (comunicaciones)
Excepcionalmente más rápido que el cifrado por bloques.
Basados en One Time Pad (*)

---

Cifrado por bloques:
Realiza el proceso de cifrado sobre bloques de texto plano de longitud fija.
La transformación sobre los bits no varía; siempre es la misma.
DES y AES son ejemplos de cifrado por bloques

---
## Add Some Slide Candy

![](assets/img/presentation.png)

---?color=linear-gradient(180deg, white 75%, black 25%)
@title[Customize Slide Layout]

@snap[west span-50]
## Customize the Layout
@snapend

@snap[east span-50]
![](assets/img/presentation.png)
@snapend

@snap[south span-100 text-white]
Snap Layouts let you create custom slide designs directly within your markdown.
@snapend

---?color=linear-gradient(90deg, #E27924 65%, white 35%)
@title[Add A Little Imagination]

@snap[north-west h4-white]
#### And start presenting...
@snapend

@snap[west span-55]
@ul[spaced text-white]
- You will be amazed
- What you can achieve
- *With a little imagination...*
- And **GitPitch Markdown**
@ulend
@snapend

@snap[east span-45]
@img[shadow](assets/img/conference.png)
@snapend

---?image=assets/img/presenter.jpg

@snap[north span-100 h2-white]
## Now It's Your Turn
@snapend

@snap[south span-100 text-06]
[Click here to jump straight into the interactive feature guides in the GitPitch Docs @fa[external-link]](https://gitpitch.com/docs/getting-started/tutorial/)
@snapend
