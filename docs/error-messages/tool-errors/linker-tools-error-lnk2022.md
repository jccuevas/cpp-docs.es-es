---
title: Las herramientas del vinculador LNK2022 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7769bc28dc777ef8d7b82b91b9695356db05a682
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300893"
---
# <a name="linker-tools-error-lnk2022"></a>Error de las herramientas del vinculador LNK2022  
  
> Error de operación de metadatos (*HRESULT*): *error_message*  
  
El vinculador detectó un error al combinar los metadatos. Los errores de metadatos deben resolverse para poder vincular correctamente.  
  
Una forma de diagnosticar este problema es ejecutar **ildasm-tokens** en los archivos objeto para averiguar qué tipos tienen los tokens enumeran en `error_message`y buscar las diferencias.  En los metadatos, los dos tipos diferentes con el mismo nombre no es válido, aun cuando el atributo LayoutType sea diferente.  
  
Una razón para LNK2022 es cuando un tipo (por ejemplo, un struct) existe en varios elementos con el mismo nombre pero con definiciones en conflicto, y cuando se compila con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  En este caso, asegúrese de que el tipo tiene una definición idéntica en todos los elementos.  El nombre del tipo aparece en `error_message`.  
  
Otra causa posible de LNK2022 es cuando el vinculador busca un archivo de metadatos en una ubicación diferente que se especificó para el compilador (con [#using](../../preprocessor/hash-using-directive-cpp.md) ). Asegúrese de que el archivo de metadatos (.dll o .netmodule) está en la misma ubicación cuando se pasa al vinculador, igual que cuando se pasó al compilador.  
  
Al compilar una aplicación de ATL, el uso de la macro `_ATL_MIXED` es necesaria en todos los elementos, si se usa en al menos uno.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente define un tipo vacío.  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Ejemplo  
  
Este ejemplo muestra que no se puede vincular dos archivos de código fuente que contienen tipos del mismo nombre pero con definiciones diferentes.  
  
El ejemplo siguiente genera el error LNK2022.  
  
```cpp  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```