---?image=assets/img/Enigma-1024x768.png
# Criptografía para @size[3em](desarrolladores)

---

#### Principios básicos

El tratamiento de la información ha requerido desde antiguo garantizar determinadas propiedades:
@snap[north-west]
autenticidad 
@snapend
@snap[north]
confidencialidad
@snapend
@snap[west]
integridad
@snapend
@snap[north-east]
disponibilidad
@snapend
@snap[east]
auditoria
@snapend
@snap[shouth]
no repudio 
@snapend
@snap[shouth-east]
existencia
@snapend

Note:

- Saber el origen de la información: autenticidad y no repudio.
- Estar seguros de que no fue modificada: integridad.
- Proteger el acceso a la información: confidencialidad 
- Asegurar el momento en que tuvo lugar: existencia.
---

### Otro

---

```java
package com.eurobits.categorizer.entity;

import java.util.List;

import com.fasterxml.jackson.annotation.JsonInclude;
import com.fasterxml.jackson.annotation.JsonInclude.Include;

import lombok.Data;

@Data
@JsonInclude(Include.NON_NULL)
public class AccountHolder {

	 private String bank;
	 private String branch;
	 private String controlDigits;
	 private String accountNumber;
	 private List<Holder> holders; 	
	 private SessionUser sessionUser;
}
```

@[1]
@[5-6]

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

Cifrado por bloques:
Realiza el proceso de cifrado sobre bloques de texto plano de longitud fija.
La transformación sobre los bits no varía; siempre es la misma.
DES y AES son ejemplos de cifrado por bloques

---

Como hemos comentado los cifrados de flujo se basan en el cifrado de un solo uso (One Time Pad) que son un modelo indescifrable (demostrado matemáticamente)
En un cifrado de un solo uso la clave es completamente aleatoria y no puede inferirse, adivinarse o deducirse, su tamaño iguala al texto a cifrar y es usada sólo una vez. 
Por ello el texto cifrado puede convertirse en todos los textos (con o sin sentido) pero sólo la clave verdadera da lugar al texto original verdadero.
Esto permite mencionar dos curiosidades:
La enorme semejanza entre este modelo y el cuento de Borges, “La Biblioteca de Babel” que relata un universo compuesto de una biblioteca de todos los libros posibles.
El Tesoro de Beale: un supuesto tesoro enterrado en torno a 1830 y cuya ubicación está detallada por un cifrado OTP. A pesar de todos los esfuerzos sigue escondido.

---

Uno de los inventos (que no descubrimiento) del S.XX
Es un sistema de cifrado basado en funciones trampa, funciones que son muy sencillas de realizar pero muy complicadas de deshacer: exponenciación modular, factorización de primos,…
Aunque teoricamente conocidas hasta que Diffie W. y M. Hellman inventaron el algoritmo que permitía el intercambio de claves.
Posteriormente se han inventado otros algoritmos algunos de los cuales sí que permiten firma o cifrado asimético: RSA, DSS, El Gamal,..
Es posible afirmar que el cifrado simétrico es el fundamento del mundo electrónico que conocemos porque es la base de la firma electrónica, la autenticación digital, el no repudio, etcétera.

---

En el algoritmo RSA tanto la codificación como la decodificación  se llevan a cabo mediante una exponenciación  en aritmética modular 
C=M^e (mod n)  
M=C^d (mod n)  siendo C el mensaje cifrado, M el mensaje original, e la clave pública (para codificar) y d la clave privada (para decodificar). Cifrar el mensaje consistirá, pues, en elevarlo a la clave pública y luego quedarse con el resto que sale al dividir por n.  Para que se cumpla esta relación, debe darse la siguiente propiedad:  e*d=1 (mod Ø(n))  donde Ø(n) es la llamada función Totient de Euler. Curiosamente, esta función es muy fácil de calcular si se conocen los factores de n, y muy difícil en el caso contrario. De hecho, si n=p*q, Ø(n)=(p-1)*(q-1). Puesto que la clave pública ha de estar constituida por el par (n,e) para que alguien pueda cifrar un mensaje, si fuera posible factorizar n, el algoritmo RSA estaría sencillamente perdido. 

---

También en criptografía, el tamaño importa.
El tamaño de las claves simétricas viene a determinar el tiempo de un ataque de fuerza bruta (probando todas las combinaciones posibles). En un cifrado OTP el tamaño es infinito, pero en un cifrado normal si tenemos una clave de 128 bits, encontraremos el texto original tras probar con 2^64 contraseñas (media).
El tamaño de los resúmenes criptográficos es una muestra de lo complicado que es lograr una colisión o una generación de un Hash a medida.
El tamaño de las claves simétricas permite medir el esfuerzo en romper la función trampa sin ayuda de la clave por fuerza bruta. Por ejemplo con un RSA de 1024 bits tenemos que hacer una factorización de un número de 309 dígitos en sus dos primos, lo cual sin ayuda del valor de la clave pública es matemáticamente complejo.

---

Quien quiera divertirse realmente con las matemáticas debe conocer el mundo de la matemática discreta y los grandes números.
Recomiendo:
Fundamentos de la Teoría de los Números de I.M. Vinogradov

---

"Códigos secretos" de Simon Singh
“Applied Cryptography” de Bruce Schneier 
“Handbook of Applied Cryptography” de A. Menezes

---

# Formatos y estándares

---

 	Ahora que parece que tenemos la herramienta básica (la criptografía asimétrica) aparecen los problemas para que se convierta en algo utilizable. Tener presente que hasta ahora hemos presentado un mundo matemático, pero su aplicación práctica es mucho más compleja. Hay que desarrollar las infraestructuras necesarias, 

Los formatos: 
¿el formato que usa Bob es el que yo entiendo?
La confianza: 
¿porqué confía Alice en Bob? ¿es esa clave pública la de Bob? ¿es Bob?
La Ley
¿qué valor legal tiene la firma electrónica?

---

La firma electrónica es uno de los ejemplos más claros de este problema: tenemos una serie de datos, estructuras de datos, que debemos intercambiar entre dos entidades.
Ambas entidades pueden estar usando sistemas diferentes y lenguajes diferentes. 
Se necesita representar esa estructura de datos en un formato común:
Un formato común para representar los datos y estructuras
Una reglas comunes para transmitirnos esta información.
Los sistemas podrán luego traducir estos formatos a sus necesidades propias.

---
#ASN.1

Abstract Syntax Notation One(notación sintáctica abstracta 1, ASN.1) es una norma para representar datos independientemente de la máquina que se esté usando y sus formas de representación internas. Es un protocolo de nivel de presentación en el modelo OSI. [Wikipedia]
Este estándar no define cómo se han de codificar esos datos, sino que es una sintaxis abstracta para indicar el significado de los datos.

---
Las codificaciones: DER, BER, CER,…
Como se ha indicado, ASN.1 no define cómo se han de codificar los datos.
La estructura una vez definida en un lenguaje común, ASN.1, debe ser codificada para poder ser almacenada y transmitida. Esto se realiza mediante:
DER (Distinguished Encoding Rules)
BER (Basic Encoding Rules)
CER (Canonical Encoding Rules)
PER (Packed Encoding Rules)
Podemos decir que DER,BER,… es la forma de codificar en un array de bytes la estructura ASN.1

---

Ejemplo
Información a intercambiar, un atributo X.500
cn=www.freesoft.org 
Mis datos en un HashMap de Java podrían ser:
HashMap commonName = new HashMap ();
commonName.put (“CN”,” www.freesoft.org”);
Pero la forma común de representarlo es la estructura en ASN.1 que define el estándar LDAP para esta información:
LDAPString ::= OCTET STRING
AttributeDescription ::= LDAPString
AttributeValueAssertion ::= SEQUENCE {
	attributeDesc AttributeDescription, 
	assertionValue AssertionValue } 
AssertionValue ::= OCTET STRING 
Usaría una librería ASN.1 para crear esta estructura y luego codificarla:
Por ejemplo…

---

Base 64
Los datos en DER/BER son un array de bytes y no pueden usarse como cadenas de texto lo que impide imprimirlos, o representarlos dentro del texto de un correo electrónico (de hecho Base64 fue desarrollado para ser utilizado con S/MIME) o incorporar estos datos binarios a estructuras XML.
Para ello tenemos la codificación en Base64. 
Base64 codifica los archivos en formato de texto ASCII
Base 64
Los 3 bytes de entrada (3x8bit) se tratan como un bloque que se divide en 4 bloques de 6 bits que se codifican cada uno en un carácter imprimible.
¿qué cosas me voy a encontrar en ASN.1?
Todo: los objetos relacionados con la firma electrónica se definen con su estructura ASN.1 codificados generalmente en DER o CER.
Todos los estándares incluyen, cuando se refieren a datos binarios, su representación en ASN.1
Los certificados x509 con extensión .cer están codificados en DER.
Los datos PKCS#7
Los almacenes de claves (PFX,P12)
Etc.
Más información…
Más sobre ASN.1 en
“A Layman's Guide to a Subset of ASN.1, BER, and DER”

Más sobre Base 64 en
http://www.aardwulf.com/tutor/base64/base64.pdf

---

<?xml ?>
Es un meta-lenguage: una manera de definir lenguajes para diferentes necesidades 
Nos lo encontraremos como formato en firma electrónica para intercambiar datos:
XMLDsig y XAdES
XML Encryption
SOAP
SAML
DSS

---

Estándares y normas
Estándares y normas
Un estándar es una especificación que regula la realización de ciertos procesos o la fabricación de componentes para garantizar la interoperabilidad.
Las normas son documentos técnico-legales con las siguientes características:
Contienen especificaciones técnicas de aplicación voluntaria. Son elaborados por consenso y están basados en los resultados de la experiencia y el desarrollo tecnológico. Son aprobados por un organismo nacional, regional o internacional de normalización reconocido.

---

Son públicas (aunque pueden no ser gratuitas).
Las normas ofrecen un lenguaje de punto común de comunicación entre las empresas, la Administración pública, los usuarios y consumidores. Las normas establecen un equilibrio socioeconómico entre los distintos agentes que participan en las transacciones comerciales, base de cualquier economía de mercado, y son un patrón necesario de confianza entre cliente y proveedor.
¿cómo resuelvo el problema de los formatos?
El mundo de la firma electrónica está inundado de estándares y  normas.
Puesto que se pretende que entidades, personas, sistemas, etc. diferentes trabajen de igual forma, entiendan la misma información y representen lo mismo de la misma forma todo está estandarizado:
 La forma de generar datos como claves, certificados, etc.
 La forma de pedir cualquier cosa y como entender la respuesta.
 La forma de representar los datos.
 La forma de intercambiar los datos.
 La forma de procesar esos datos.
 ….

---

JWT JWS

---

OAuth2

---

TLS

---

Estandarización 
Algunos estándares:
CAdES (CMS Advanced Electronic Signatures). ETSI TS 101 733 CAdES version 1.7.4 from Jul, 2008, XAdES (XML Advanced Electronic Signatures). ETSI TS 101 903 XAdES version 1.4.1 from 2009-06-15, PAdES (PDF Advanced Electronic Signatures). ETSI TS 102778, RFC 2560 “Online Certificate Status Protocol – OCSP”, RFC 3126 “Electronic Signature Formats for long term electronic signatures”, RFC 2630 ”Cryptographic Message Syntax”,RFC 2634 ”Enhanced Security Services for S/MIME”, RFC 5126 “CMS Advanced Electronic Signatures (CAdES)”,RFC 3280 ”Certificate and Certificate Revocation List (CRL) Profile”,RFC 3275  “(Extensible Markup Language) XML-Signature Syntax and Processing ”, RFC 2797  “Certificate Management Messages over CMS”,RFC 2585  “Operational Protocols: FTP and HTTP”, RFC 3161  “Time-Stamp Protocol (TSP)”, RFC 3029 “Data Validation and Certification Server Protocols”, RFC 3852  “Cryptographic Message Syntax” (deja obsoletos los RFC3369, RFC 3211, RFC 2630, RFC 2315-PKCS #7 version 1.5-), RFC 4853 - (Actualización Marzo 2008) “Cryptographic Message Syntax – Multiple Signer Clarification”, CWA 15579  E-invoices and digital signatures, ETSI TS 102 042 Policy requirements for CA issuing PKC, ETSI TS 102 023 Policy Requirements for Time Stamping Authorities Certificates for Electronic Signatures – Part 1: System Security Requirements, ETSI TS 102 231 Provision of harmonized Trust Service Provider status information (TSL), ETSI TS 102 280 X.509 V.3 Certificate Profile for Certificates Issued to Natural Persons, ETSI TS 102 158 Policy requirements for Certification Service Providers issuing attribute certificates usable with Qualified certificates, ETSI TS 101 861 V1.2.1  Time stamping profile, CEN / ISSS CWA 14167-2 Cryptographic module for CSP signing operations with backup – Protection profile – CMCSOB PP, CEN / ISSS CWA 14167-3 Cryptographic module for CSP key generation services protection profile CMCKG-PP, CEN / ISSS CWA 14167-4 Cryptographic module for CSP signing operations – Protection profile – CMCSO PP, CEN / ISSS CWA 14169 Secure signature-creation devices “EAL 4+”, CEN / ISSS CWA 14170 Security requirements for signature creation applications, CEN / ISSS CWA 14171 General Guidelines for Electronic Signature Verification, CEN / ISSS CWA 14172 EESSI Conformity Assessment Guidance (8 parts), CEN / ISSS CWA 14355 Guidelines for the implementation of Secure Signature-Creation Devices, CEN / ISSS CWA 14365-1 Guide on the Use of Electronic Signatures – Part 1: Legal and Technical Aspects, CEN / ISSS CWA 14365-2 Guide on the Use of Electronic Signatures – Part 2: Protection Profile for Software Signature Creation Devices, CEN / ISSS CWA 14167-1 Security Requirements for Trustworthy Systems Managing, CEN / ISSS CWA 14890-1 Application Interface for smart cards used as Secure Signature Creation Devices – Part 1: Basic requirements, CEN / ISSS CWA 14890-2 Application Interface for smart cards used as Secure Signature Creation Devices – Part 2: Additional Services, TR 102 047 (International Harmonization of Electronic Signature Formats) FIPS PUB 180-1 (Secure Hash Standard), ISO 32000,……..
Terceras Partes de Confianza
“El mayor despeñadero, la confianza” Francisco de Quevedo 
Para resolver el problema de la confianza la firma electrónica se basa en las Terceras Partes de Confianza.
Una TPC es una Autoridad de Certificación, Sellado, Validación, etcétera y que, como su nombre indica, actúa como tercera parte en la que ambos agentes confían.

La base para trabajar y gestionar esta confianza son los Certificados Electrónicos.
Un certificado digital es un documento digital mediante el cual un tercero confiable (una Autoridad de Certificación) garantiza la vinculación entre la identidad de un sujeto o entidad y su clave pública
Certificados electrónicos: x509v3
El formato x509v3 define la forma en que se debe representar un certificado electrónico. Se define en el estándar RFC 5280 (antes 3280, 4325 y 4630 ). 
Como es habitual define todas las estructuras de datos en ASN.1
La estructura de un certificado digital X.509 v3 es la siguiente:
Versión 
Número de serie 
ID del algoritmo 
Emisor 
Validez 
No antes de 
No después de 
Sujeto (objeto certificado)
Información de clave pública del sujeto 
Algoritmo de clave pública 
Clave pública del sujeto 
Identificador único de emisor (opcional) 
Identificador único de sujeto (opcional) 
Extensiones (opcional) 
... 
Algoritmo usado para firmar el certificado 
Firma digital del certificado 
Donde se puede esconder un certificado
*.CER = sólo el certificado [y puede que la cadena] en formato DER.
PKCS7 = puede tener el certificado en un SignedData.
PKCS12 = tendrá el certificado junto a la parte privada.
XMLDsig = indica en varios apartados los certificados en DER/B64
SSL = en una conexión SSL se transmiten certificados
TrustStores & KeyStores Java
Microsoft Management Console / Certificates
En el DNIe, en la tarjeta de CERES,…
…..
¿cómo se obtiene un certificado?
El suscriptor (Subject) genera sus claves y una petición de certificado que incluye sus datos y su clave pública
Acude a una Autoridad de Registro y demuestra que es quién dice ser en el certificado
La AR indica a la Autoridad emisora que se puede firmar ese certificado
La CA emite un certificado electrónico
El usuario ya puede descargarse el certificado
Cadena de confianza
 Se suelen construir cadenas de confianza.
Una AC raíz emite certificados a AC intermedias que son las responsables de la emisión de los certificados finales.
¡acción!
Ejemplo Java de leer un certificado
Ejemplo de un certificado en ASN.1
Ejemplo en Base64 extraído de un XMLDsig
La Arquitectura Criptográfica de Java (JCA/JCE)
La distribución estándar de Java (J2SE) incluye un framework para criptografía conocido como JCE/JCE (JCE se distribuía antes separadamente, ahora van juntos).
Este framework permite acceder de forma común a todas las funciones criptográficas, con independencia del proveedor. Para ello tiene un motor (factoría) que proporciona el proveedor que mejor puede resolver la función solicitada.
Incluye 2 clases auxiliares (Provider,Security) y los motores de:
MessageDigest, Signature, KeyPairGenerator, KeyFactory, AlgorithmParameters, AlgorithmParameterGenerator, CertificateFactory, KeyStore, SecureRandom, CertPathBuilder, CertPathValidator, CertStore. 
JCA/JCE en J2SE 5
Support for Additional Features of PKCS #11 
Integration with Solaris Cryptographic Framework
Support for ECC Algorithm 
Added ByteBuffer API Support to JCA/JCE 
Support for RC2ParameterSpec 
Full support for XML Encryption RSA-OAEP Algorithm 
Simplified retrieval of PKCS8EncodedKeySpec from javax.crypto.EncryptedPrivateKeyInfo 
Support for "PBEWithSHA1AndDESede" and "PBEWithSHA1AndRC2_40" Ciphers 
Support for XML Encryption Padding Algorithm in JCE Block Encryption Ciphers 
Ability to Dynamically Determine Maximum Allowable Key Length
Support for RSA encryption to SunJCE provider 
Support for RC2 and ARCFOUR Ciphers to SunJCE provider 
Support for HmacSHA256, HmacSHA384 and HmacSHA512 
Proveedores criptográficos
Los proveedores deben estar instalados de forma estática (java.security) o pueden instanciarse dinámicamente mediante métodos del propio Provider.
Ejemplo IAIK.addAsJDK14Provider();

Uso de un proveedor para generar resúmenes:
MessageDigest md =  MessageDigest.getInstance(String algorithm, String provider);
Otras APIs :: JSR105 & JSR106
JSR-105 estandariza la tecnología de firma XML en Java (XMLDSig). Está incorporado en Java SE 6 que además incluye un proveedor del interfaz 105.
Otros proyectos, por ejemplo Apache Santuario (XML Security) proporcionan implementaciones que usan este interfaz.
Por otro lado JSR-106 se encarga de definir un interfaz común para XML Encryption.
En detalle
El proceso de firma electrónica básico (sobre electrónico)
Formatos para emitir firmas electrónicas
Existen diferentes formatos para almacenar una firma digital.
La mayoría encapsula en un sobre electrónico los datos, la identidad del firmante y la firma.
Algunos ejemplos de formatos son:
Privacy-Enhanced Mail (PEM) – RFC 1421 
PKCS#7 / CMS
XMLDsig
Formatos básicos de firma
Es uno de los formatos tradicionales más extendidos
Se podría decir que CMS es la evolución de PKCS#7, son prácticamente idénticos, los trataremos de forma común, ya que existe gran compatibilidad entre ambos.
No obstante, la referencia debe ser el estándar CMS a partir de los estándares de IETF, sobre todo, del RFC 3852.
Se suele emplear en aplicaciones de escritorio.
Se trata de un formato de encapsulamiento codificado en ASN.1 y a veces también en Base64.
Habitualmente, una firma en CMS puede representarse en su modalidad Attached o Dettached, en función de que incluya o no el propio documento. La más habitual suele ser la Attached.
CMS permite incluir diferentes firmantes en la firma bajo dos modalidades: encadenada y mancomunada. PKCS#7 no permite esta estructura de firma.
La firma propiamente dicha es un compendio de datos formales referidos al tipo de firma (algoritmos, versiones, ...) así como de atributos firmados (signed) y no firmados (unsigned) bajo una estructura dada.

Attached versus Detached
Firma de Archivos Completos  Firma separada
Dos ficheros que gestionar
Mantenerlos enlazados de alguna manera
Los dos son necesarios para la verificación
Las aplicaciones pueden acceder a los datos sin verificar la firma
Formatos básicos de firma 
Formatos básicos de firma 
Formatos básicos de firma 

Existen diferentes problemas asociados a la perdurabilidad de las firmas realizadas a lo largo del tiempo, siendo el más importante el de la validación de las firmas a largo plazo.
En la actualidad se realizan la mayoría de las firmas realizando únicamente una comprobación de la CRL/OCSP en el momento de realizar la firma, pero no se guarda evidencia de la misma.
En el futuro, cuando se quiera comprobar la validez de la firma y el certificado ya esté caducado o revocado no se podrá determinar si en el momento de firmar el certificado (y por tanto la firma) era válida.
Para solucionar este inconveniente se precisa incorporar a la firma electrónica los elementos de tiempo y validación que permitan verificar esa firma sin ayuda externa
El fin último es crear una firma “completa” y “auto verificable”.
Hasta llegar a este fin último, se puede pasar por estados intermedios que mejoren la calidad de estas firmas. 
El Sello de Tiempo 
Garantiza la existencia de un documento antes de un momento de tiempo
TimeStamping 
Firma longeva
El proceso de verificación de una firma debe poder repetirse, incluso años después de su generación. 
El certificado puede no ser válido años después, pero sí lo era en el momento de la firma; más aún, los algoritmos, claves y otros elementos criptográficos pueden llegar a ser vulnerables, se considera que las evidencias electrónicas son de carácter temporal, siendo necesaria su renovación (ésto es, las evidencias que en su día eran válidas dejan de serlo a partir de un momento determinado).
La solución de este problema se explica en la RFC 3126 de IETF (Internet Engineering Task Force) del 2001, también adoptada en los estándares XAdES y CAdES de ETSI (European Telecommunications Standards Institute).
Formatos Avanzados de Firma 
Firma Sencilla
Formatos de firma avanzados
OASIS Digital Signature Services
El capítulo DSS define sus objetivos:
Desarrollar “un protocolo para un Web Service de creación de firmas digitales. Proveyendo firmas digitales vía dicho Web Service facilita el control basado en políticas de la provisión de firmas.
Desarrollar “un protocolo para un Web Service de verificación de firmas digitales que permita verificar firmas en relación a un conjunto de políticas dado”.
Desarrollar “un protocolo basado en XML para emitir Sellos de Tiempo criptográficos”. 


SSL
SSL Handshake
Configuración SSL en WAS 61
El entorno legal
La Firma Electrónica
Artilugio legal que busca la equivalencia de la firma manuscrita
Normativa Básica:
Directiva 1999/93/CE del Parlamento Europeo y del Consejo, de 13 de diciembre de 1999, por la que se establece un marco comunitario para la firma electrónica
Ley 59/2003, de 19 de diciembre, de firma electrónica.
Tipos de Firma Electrónica
Simple
“… conjunto de datos … que pueden ser utilizados como medio de identificación del firmante” (Art 3.1 Ley 59/2003)

Avanzada
Simple + “y detectar cualquier cambio ulterior de los datos firmados, que está vinculada al firmante de manera única y a los datos a que se refiere y que ha sido creada por medios que el firmante puede mantener bajo su exclusivo control” (Art 3.2 Ley 59/2003)

Cualificada (Reconocida)
Avanzada + “basada en un certificado reconocido (cualificado) y generada mediante un dispositivo seguro de creación de firma” (Art 3.3 Ley 59/2003)
Presunción de validez
Directiva 1999/93/CE
Artículo 5 (Efectos legales): Los Estados miembros velarán por que no se niegue efecto legal, validez ni obligatoriedad a una firma electrónica por el hecho de que ésta se presente en forma electrónica. 


Artículo 3, de la Ley de Firma Electrónica:
4. La firma electrónica reconocida tendrá respecto de los datos consignados en forma electrónica el mismo valor que la firma manuscrita en relación con los consignados en papel.
Prestador de Servicios de Certificación
“Se denomina prestador de servicios de certificación la persona física o jurídica que expide certificados electrónicos o presta otros servicios en relación con la firma electrónica” (Art. 2.2 Ley 59/2003)
Autoridades de Certificación
Autoridades de Sello de Tiempo
Autoridades de Validación
Otros
Certificados Cualificados (reconocidos)
Incluirán, al menos, los siguientes datos:
La indicación de que se expiden como tales.
El código identificativo único del certificado.
La identificación del PSC que expide el certificado y su domicilio.
La firma electrónica avanzada del PSC que expide el certificado.
La identificación del firmante …
Los datos de verificación de firma … (la clave pública)
El comienzo y el fin del período de validez del certificado.
Los límites de uso del certificado, si se establecen.
Los PSC deberán:
Comprobar la identidad y circunstancias …
Verificar que la información del certificado es exacta.
Asegurarse que el firmante está en posesión de los datos de creación de firma (la clave privada).
Titulares de los Certificados Cualificados

Conforme a la Directiva 1999/93 solo pueden ser firmantes las personas físicas, actuando en nombre propio o en representación de una entidad. 
Conforme a la Ley 59/2003, de firma electrónica:
Las personas físicas, actuando en nombre propio o en representación de una entidad.
Las personas jurídicas
Las entidades carentes de personalidad jurídica a las que se refiere el actual artículo 35.4 LGT
Prestadores Registrados
Herramientas 
De escritorio
Otras herramientas que viene bien tener a mano
eCofirma
ASN1Decoder
clickSign
eFactura MICyT
Plataformas de Firma
Se hace necesario disponer de sistemas que permitan gestionar la complejidad:
Gestionar certificados de distintas CAs
Gestinar distintos formatos de firma (ASN.1, XML – Sencillas/Completas)
Gestionar Sellos de Tiempo
En este terreno tenemos las siguientes plataformas y tecnologías:
GISS (SIAVAL)
ISCII (ASF)
@firma (propia)
PLATINO (ASF)
ZAIN (IZENPE)
CATCert (SafeLayer)


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
