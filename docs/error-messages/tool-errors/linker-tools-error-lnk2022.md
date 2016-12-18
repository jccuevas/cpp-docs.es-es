---
title: "Error de las herramientas del vinculador LNK2022 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2022"
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error en la operación con metadatos \(HRESULT\) : mensaje\_de\_error  
  
 El vinculador detectó un error al combinar metadatos.  Los errores de metadatos deben resolverse para poder vincular correctamente.  
  
 Una forma de diagnosticar este problema es ejecutar **ildasm –tokens** en los archivos objeto para averiguar qué tipos tienen los tokens incluidos en la lista `error_message` y buscar diferencias.  En metadatos, no se consideran válidos dos tipos diferentes con el mismo nombre, aun cuando el atributo LayoutType sea diferente.  
  
 Una causa del error LNK2022 es cuando un tipo \(como un struct\) existe en distintas operaciones de compilación con el mismo nombre, pero con definiciones en conflicto, y se compila con la opción [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  En este caso, asegúrese de que el tipo tiene una definición idéntica en todas las operaciones de compilación.  El nombre de tipo se muestra en `error_message`.  
  
 Otra causa posible para que se produzca el error LNK2022 es cuando el vinculador encuentra un archivo de metadatos en una ubicación distinta de la especificada para el compilador \(con [\#using](../../preprocessor/hash-using-directive-cpp.md)\).  Asegúrese de que el archivo de metadatos \(.dll o .netmodule\) está en la misma ubicación cuando se dedica al vinculador, tal y como estaba cuando se pasó al compilador.  
  
 Al generar una aplicación ATL, el uso de [\_ATL\_MIXED](../Topic/_ATL_MIXED.md) se requiere en todas las operaciones de compilación, si se utiliza por lo menos en una.  
  
## Ejemplo  
 El ejemplo siguiente define un tipo vacío.  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## Ejemplo  
 Este ejemplo muestra que no se pueden vincular dos archivos de código fuente que contienen tipos del mismo nombre pero con definiciones diferentes.  
  
 El ejemplo siguiente genera el error LNK2022.  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```