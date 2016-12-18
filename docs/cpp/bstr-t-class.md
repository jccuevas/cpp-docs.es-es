---
title: "_bstr_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t (clase)"
  - "BSTR (objeto)"
  - "BSTR (objeto), encapsulación COM"
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Un objeto `_bstr_t` encapsula el [tipo de datos BSTR](http://msdn.microsoft.com/es-es/1b2d7d2c-47af-4389-a6b6-b01b7e915228).  La clase administra la asignación y desasignación de recursos con llamadas de función a **SysAllocString** y **SysFreeString** y otras API de `BSTR` cuando es necesario.  La clase `_bstr_t` utiliza el recuento de referencias para evitar una sobrecarga excesiva.  
  
### Construcción  
  
|||  
|-|-|  
|[\_bstr\_t](../cpp/bstr-t-bstr-t.md)|Construye un objeto `_bstr_t`.|  
  
### Operaciones  
  
|||  
|-|-|  
|[Assign](../cpp/bstr-t-assign.md)|Copia un valor `BSTR` en el valor `BSTR` contenido en `_bstr_t`.|  
|[Attach](../cpp/bstr-t-attach.md)|Vincula un contenedor `_bstr_t` a un `BSTR`.|  
|[copy](../cpp/bstr-t-copy.md)|Crea una copia del objeto `BSTR` encapsulado.|  
|[Desasociar](../cpp/bstr-t-detach.md)|Devuelve el `BSTR` contenido en `_bstr_t` y desasocia `BSTR` de `_bstr_t`.|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|Apunta al `BSTR` contenido en `_bstr_t`.|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Señala al principio del objeto `BSTR` incluido en `_bstr_t`.|  
|[length](../cpp/bstr-t-length.md)|Devuelve el número de caracteres de `_bstr_t`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../cpp/bstr-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_bstr_t` existente.|  
|[operador \+\=](../cpp/bstr-t-operator-add-equal-plus.md)|Agrega caracteres al final del objeto `_bstr_t`.|  
|[operador \+](../cpp/bstr-t-operator-add-equal-plus.md)|Concatena dos cadenas.|  
|[operador \!](../cpp/bstr-t-operator-logical-not.md)|Comprueba si el `BSTR` encapsulado es una cadena **NULL**.|  
|[operador \=\=, \!\=, \<, \>, \<\=, \>\=](../cpp/bstr-t-relational-operators.md)|Compara dos objetos `_bstr_t`.|  
|[operador wchar\_t\* &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrae los punteros al objeto `BSTR` multibyte o Unicode encapsulado.|  
  
## FIN de Específicos de Microsoft  
  
## Requisitos  
 **Encabezado:** comutil.h  
  
 **Lib:** omsuppw.lib o comsuppwd.lib \(vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información\)  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)