---
title: "Usar los operadores CArchive &lt;&lt; y &gt;&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive (clase), operadores"
  - "CArchive (clase), almacenar y cargar objetos"
  - "objetos [C++], cargar a partir de valores almacenados previamente"
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar los operadores CArchive &lt;&lt; y &gt;&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CArchive` proporciona \<\< y \>\> operadores para escribir y leer tipos de datos simples así como s de `CObject`en un archivo.  
  
#### Para almacenar un objeto en un archivo con un archivo  
  
1.  El ejemplo siguiente muestra cómo almacenar un objeto en un archivo con un archivo:  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### Para cargar un objeto de un valor almacenado previamente en un archivo  
  
1.  El ejemplo siguiente muestra cómo cargar un objeto de un valor almacenado previamente en un archivo:  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 Normalmente, se almacena y carga datos en un archivo con un archivo en las funciones de `CObject`\- clases derivadas de `Serialize` , que debe tener declarado con la macro de **DECLARE\_SERIALIZE** .  Una referencia a un objeto de `CArchive` se pasa a la función de `Serialize` .  Se llama a la función de `IsLoading` del objeto de `CArchive` para determinar si la función de `Serialize` se ha denominado para cargar datos de archivo o de almacén al archivo.  
  
 La función de `Serialize` de `CObject`serializable \(la clase derivada tiene normalmente el formato siguiente:  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 La plantilla anterior de código es exactamente igual que el AppWizard crea para la función de `Serialize` de documentos \(una clase derivada de **CDocument\)**.  Ayuda de esta plantilla de código escribe código que es más fácil de ver, porque el código que almacena y el código de carga siempre deben ser paralelos, como en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 La biblioteca define **\<\<** y operadores de **\>\>** para `CArchive` como el primer operando y los tipos de datos y los tipos de clase siguientes como el segundo operando:  
  
||||  
|-|-|-|  
|`CObject*`|**CALIBRE y CSize**|**float**|  
|**WORD**|`CString`|**POINT** y `CPoint`|  
|`DWORD`|**BYTE**|`RECT` y `CRect`|  
|**Double**|**LONG**|`CTime` y `CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  Almacenar y cargar s para `CObject`mediante un archivo requiere la consideración adicional.  Para obtener más información, vea [Almacenar y cargando CObjects mediante un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Los operadores de **CArchive \<\<** y de **\>\>** siempre devuelven una referencia al objeto de `CArchive` , que es el primer operando.  Esto permite encadenar los operadores, como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## Vea también  
 [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)