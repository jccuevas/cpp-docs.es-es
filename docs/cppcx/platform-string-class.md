---
title: "Platform::String (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String"
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::String (Clase)
Representa una cadena es una colección secuencial de caracteres Unicode que se utiliza para representar texto. Para obtener más información y ejemplos, vea [Cadenas](../cppcx/strings-c-cx.md).  
  
## Sintaxis  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## Iteradores  
 Dos funciones de iterador, que no son miembros de la clase String, se pueden utilizar con la función de plantilla de `std::for_each` para enumerar los caracteres de un objeto String.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|`const char16* begin(String^ s)`|Devuelve un puntero al principio del objeto String especificado.|  
|`const char16* end(String^ s)`|Devuelve un puntero después del final del objeto String especificado.|  
  
## Miembros  
 La clase String hereda de Object y las interfaces IDisposable, IEquatable e IPrintable.  
  
 La clase String también tiene los siguientes tipos de miembros.  
  
 **Constructores**  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[String::String \(Constructor\)](../cppcx/string-string-constructor.md)|Inicializa una nueva instancia de la clase String.|  
  
 **Métodos**  
  
 La clase String hereda los métodos Equals\(\), Finalize\(\), GetHashCode\(\), GetType\(\), MemberwiseClose\(\) y ToString\(\) de [Platform::Object \(Clase\)](../cppcx/platform-object-class.md). String también tiene los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[String::Begin \(Método\)](../cppcx/string-begin-method.md)|Devuelve un puntero al principio de la cadena actual.|  
|[String::CompareOrdinal \(Método\)](../cppcx/string-compareordinal-method.md)|Compara dos objetos `String` mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores alfanuméricos representados por los objetos.|  
|[String::Concat \(Método\)](../cppcx/string-concat-method.md)|Concatena los valores de dos objetos String.|  
|[String::Data \(Método\)](../cppcx/string-data-method.md)|Devuelve un puntero al principio de la cadena actual.|  
|[String::Dispose \(Método\)](../cppcx/string-dispose-method.md)|Libera recursos.|  
|[String::End \(Método\)](../cppcx/string-end-method.md)|Devuelve un puntero después del final de la cadena actual.|  
|[String::Equals \(Método\)](../cppcx/string-equals-method.md)|Indica si el objeto especificado es igual al objeto actual.|  
|[String::GetHashCode \(Método\)](../cppcx/string-gethashcode-method.md)|Devuelve el código hash de esta instancia.|  
|[String::IsEmpty \(Método\)](../cppcx/string-isempty-method.md)|Indica si el objeto String actual está vacío.|  
|[String::IsFastPass \(Método\)](../cppcx/string-isfastpass-method.md)|Indica si el objeto String actual participa en una operación *rápida de paso*. En una operación rápida de paso, se suspende el recuento de referencias.|  
|[String::Length \(Método\)](../cppcx/string-length-method.md)|Recupera la longitud del objeto String actual.|  
|[String::ToString \(Método\)](../cppcx/string-tostring-method-c-cx.md)|Devuelve un objeto String cuyo valor es igual al de la cadena actual.|  
  
 **Propiedades**  
  
 La clase String tiene las propiedades siguientes.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[Operador String::operator\=\=](../cppcx/string-operator-equality-operator-c-cx.md)|Indica si dos objetos String especificados tienen el mismo valor.|  
|[operator\+ \(Operador\)](../cppcx/string-operator-decrementoperator.md)|Concatena dos objetos String en un nuevo objeto String.|  
|[Operador String::operator\>](../cppcx/string-operator-greater-than-operator-c-cx.md)|Indica si el valor de un objeto String es mayor que el valor de un segundo objeto String.|  
|[Operador String::operator\>\=](../cppcx/string-operator-greater-than-or-equals-c-cx.md)|Indica si el valor de un objeto String es mayor o igual que el valor de un segundo objeto String.|  
|[Operador String::operator\!\=](../cppcx/string-operator-inequality-operator-c-cx.md)|Indica si dos objetos String especificados tienen valores diferentes.|  
|[Operador String::operator\<](../cppcx/string-operator-less-than-operator-c-cx.md)|Indica si el valor de un objeto String es menor que el valor de un segundo objeto String.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado** vccorlib.h \(incluido de forma predeterminada\)  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)