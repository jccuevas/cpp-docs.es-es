---
title: "basic_istream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_istream"
  - "istream/std::basic_istream"
  - "std::basic_istream"
  - "std.basic_istream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istream (clase)"
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# basic_istream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia con elementos de tipo `Elem`, también conocido como [char\_type](../Topic/basic_ios::char_type.md), cuyos rasgos de caracteres están determinados por la clase *Tr*, también conocida como [traits\_type](../Topic/basic_ios::traits_type.md).  
  
## Sintaxis  
  
```  
  
     template <class   
     Elem  
     , class   
     Tr  
      = char  
     _  
     traits<  
     Elem  
     > >  
class basic_istream  
   : virtual public basic_ios<Elem, Tr>  
```  
  
## Comentarios  
 La mayoría de las funciones miembro que sobrecargan [operador\>\>](../Topic/basic_istream::operator%3E%3E.md) son funciones de entrada con formato.  Siguen el patrón:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);  
if (ok)  
    {try  
        {<extract elements and convert  
        accumulate flags in state  
        store a successful conversion> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
return (*this);  
```  
  
 Muchas otras funciones miembro son funciones de entrada sin formato.  Siguen el patrón:  
  
```  
iostate state = goodbit;  
count = 0;    // the value returned by gcount  
const sentry ok(*this, true);  
if (ok)  
    {try  
        {<extract elements and deliver  
        count extracted elements in count  
        accumulate flags in state> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
```  
  
 Ambos grupos de funciones llaman a [setstate](../Topic/basic_ios::setstate.md)\(**eofbit**\) si encuentran el final del archivo al extraer los elementos.  
  
 Un objeto de clase `basic_istream`\<`Elem`, *Tr*\> almacena:  
  
-   Un objeto base público virtual de clase [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, *Tr*\>`.`  
  
-   Un recuento de extracción para la última operación de entrada sin formato \(llamada **count** en el código anterior\).  
  
## Ejemplo  
 Vea el ejemplo de la [basic\_ifstream \(Clase\)](../standard-library/basic-ifstream-class.md) para obtener más información sobre los flujos de entrada.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_istream](../Topic/basic_istream::basic_istream.md)|Construye un objeto de tipo `basic_istream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[gcount](../Topic/basic_istream::gcount.md)|Devuelve el número de caracteres leídos durante la última entrada sin formato.|  
|[get](../Topic/basic_istream::get.md)|Lee uno o varios caracteres del flujo de entrada.|  
|[getline](../Topic/basic_istream::getline.md)|Lee una línea del flujo de entrada.|  
|[omitir](../Topic/basic_istream::ignore.md)|Hace que se omita una serie de elementos desde la posición de lectura actual.|  
|[peek](../Topic/basic_istream::peek.md)|Devuelve el siguiente carácter que se debe leer.|  
|[putback](../Topic/basic_istream::putback.md)|Coloca un carácter especificado en la secuencia.|  
|[read](../Topic/basic_istream::read.md)|Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.|  
|[readsome](../Topic/basic_istream::readsome.md)|Solo lee del búfer.|  
|[seekg](../Topic/basic_istream::seekg.md)|Mueve la posición de lectura de una secuencia.|  
|[sentry](../Topic/basic_istream::sentry.md)|La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.|  
|[swap](../Topic/basic_istream::swap.md)|Intercambia este objeto `basic_istream` por el parámetro del objeto `basic_istream` proporcionado.|  
|[sync](../Topic/basic_istream::sync.md)|Sincroniza el dispositivo de entrada asociado a la secuencia con el búfer de la secuencia.|  
|[tellg](../Topic/basic_istream::tellg.md)|Notifica la posición de lectura actual en la secuencia.|  
|[unget](../Topic/basic_istream::unget.md)|Devuelve el último carácter leído a la secuencia.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \>\>](../Topic/basic_istream::operator%3E%3E.md)|Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.|  
|[operador \=](../Topic/basic_istream::operator=.md)|Asigna a este objeto el `basic_istream` de la parte derecha del operador.  Se trata de una asignación de movimiento con una referencia `rvalue` que no deja ninguna copia.|  
  
## Requisitos  
 **Encabezado:** \<istream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)