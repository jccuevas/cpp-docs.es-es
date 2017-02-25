---
title: "basic_ostream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_ostream"
  - "std.basic_ostream"
  - "ostream/std::basic_ostream"
  - "basic_ostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ostream (clase)"
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ostream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo con elementos de tipo **Elem**, también conocido como [char\_type](../Topic/basic_ios::char_type.md), cuyos rasgos de caracteres están determinados por la clase **Tr**, también conocida como [traits\_type](../Topic/basic_ios::traits_type.md).  
  
## Sintaxis  
  
```  
  
template <class   
_Elem  
, class   
_Tr  
 = char  
_  
traits<Elem> >  
   class basic  
_  
ostream  
       : virtual public basic  
_  
ios<  
_Elem  
,   
_Tr  
>  
  
```  
  
#### Parámetros  
 `_Elem`  
 Objeto `char_type`.  
  
 `_Tr`  
 El carácter `traits_type`.  
  
## Comentarios  
 La mayoría de las funciones miembro que sobrecargan [operador\<\<](../Topic/basic_ostream::operator%3C%3C.md) son funciones de salida con formato. Siguen el patrón:  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( ok )  
   {try  
      {<convert and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
        {setstate( badbit ); }  
      catch ( ... )  
        {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
        throw; }}  
width( 0 );    // Except for operator<<(Elem)  
setstate( state );  
return ( *this );  
```  
  
 Otras dos funciones miembro son funciones de salida sin formato. Siguen el patrón:  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( !ok )  
   state |= badbit;  
else  
   {try  
      {<obtain and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
         {setstate( badbit ); }  
      catch ( ... )  
         {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
         throw; }}  
setstate( state );  
return ( *this );  
```  
  
 Ambos grupos de funciones llaman a [setstate](../Topic/basic_ios::setstate.md)\(**badbit**\) si encuentran un error al insertar elementos.  
  
 Un objeto de clase basic\_istream\<**Elem**, **Tr**\> solo almacena un objeto base público virtual de clase [basic\_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr\>**.  
  
## Ejemplo  
 Vea el ejemplo de [basic\_ofstream \(Clase\)](../standard-library/basic-ofstream-class.md) para obtener más información acerca de los flujos de salida.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_ostream](../Topic/basic_ostream::basic_ostream.md)|Construye un objeto `basic_ostream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[flush](../Topic/basic_ostream::flush.md)|Vacía el búfer.|  
|[put](../Topic/basic_ostream::put.md)|Coloca un carácter en una secuencia.|  
|[seekp](../Topic/basic_ostream::seekp.md)|Restablece la posición en el flujo de salida.|  
|[sentry](../Topic/basic_ostream::sentry.md)|La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.|  
|[swap](../Topic/basic_ostream::operator=.md)|Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.|  
|[tellp](../Topic/basic_ostream::tellp.md)|Notifica la posición en el flujo de salida.|  
|[escribir](../Topic/basic_ostream::write.md)|Coloca los caracteres en una secuencia.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_ostream::operator=.md)|Asigna el valor del parámetro de objeto `basic_ostream` a este objeto.|  
|[operator\<\<](../Topic/basic_ostream::operator%3C%3C.md)|Escribe en la secuencia.|  
  
## Requisitos  
 **Encabezado:** \<ostream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)