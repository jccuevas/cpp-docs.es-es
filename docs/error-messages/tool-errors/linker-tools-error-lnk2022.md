---
title: Las herramientas del vinculador LNK2022 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 91fb85679fd6c66bc97974912a2de688f494d5e9
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2022"></a>Error de las herramientas del vinculador LNK2022
Error de operación de metadatos (HRESULT): error_message  
  
 El vinculador ha detectado un error al combinar metadatos. Los errores de metadatos deben resolverse para poder vincular correctamente.  
  
 Una forma de diagnosticar este problema es ejecutar **ildasm – tokens** en los archivos objeto para averiguar qué tipos tienen los tokens enumeran en `error_message`y ver las diferencias.  En los metadatos, los dos tipos diferentes con el mismo nombre no es válido, aun cuando el atributo LayoutType sea diferente.  
  
 Una razón para LNK2022 es cuando un tipo (como un struct) existe en distintas operaciones de compilación con el mismo nombre pero con definiciones en conflicto, y se compila con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  En este caso, asegúrese de que el tipo tiene una definición idéntica en todos los elementos.  El nombre del tipo aparece en `error_message`.  
  
 Otra causa posible error LNK2022 es cuando el vinculador encuentra un archivo de metadatos en una ubicación diferente que se especificó para el compilador (con [#using](../../preprocessor/hash-using-directive-cpp.md) ). Asegúrese de que el archivo de metadatos (.dll o .netmodule) está en la misma ubicación cuando se pasa al vinculador, tal como estaba cuando se pasó al compilador.  
  
 Al crear una aplicación ATL, el uso de [_ATL_MIXED](http://msdn.microsoft.com/Library/11b59a83-7098-43e2-9f7b-408299930966) es necesario en todos los elementos, si se utiliza en al menos uno.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente define un tipo vacío.  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra que no se puede vincular dos archivos de código fuente que contienen tipos del mismo nombre pero con definiciones diferentes.  
  
 En el ejemplo siguiente genera el error LNK2022.  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```
