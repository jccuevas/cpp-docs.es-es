---
title: "Archivos en MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acceso binario"
  - "acceso binario, operaciones en archivo binario de MFC"
  - "clases de archivos E/S [C++]"
  - "archivos [C++], manipular"
  - "archivos [C++], MFC"
  - "archivos [C++], serialización"
  - "E/S [C++], clases MFC"
  - "E/S [MFC]"
  - "MFC [C++], operaciones en archivo"
  - "persistencia [C++]"
  - "serialización [C++], MFC (archivos)"
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la biblioteca Microsoft Foundation Class \(MFC\), la clase [Archivo C](../mfc/reference/cfile-class.md) controla las operaciones de E\/S de archivo normal.  Esta familia de casos explica cómo abrir y cerrar los archivos así como datos de lectura y escritura a estos archivos.  También explica operaciones de estado del archivo.  Para obtener una descripción de cómo utilizar las características basadas objeto de serialización de MFC como una manera alternativa de datos de lectura y escritura en archivos, vea el artículo [Serialización](../mfc/serialization-in-mfc.md).  
  
> [!NOTE]
>  Si utiliza objetos MFC **CDocument** , el marco hace gran parte del trabajo de serialización para usted.  En particular, el marco de trabajo crea y utiliza el objeto de `CFile` .  Tiene que escribir sólo código de reemplazo de la función miembro de `Serialize` de la clase **CDocument**.  
  
 La clase de `CFile` proporciona una interfaz para las operaciones de uso general del archivo binario.  Las clases de `CStdioFile` y de `CMemFile` derivadas de `CFile` y la clase de `CSharedFile` derivada de `CMemFile` proporcionan servicios de archivo especializados.  
  
 Para obtener más información sobre alternativas al archivo de MFC que administra, vea [El control de archivo](../c-runtime-library/file-handling.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
 Para obtener información sobre las clases derivadas de `CFile` , vea [Gráfico de jerarquía de MFC](../mfc/hierarchy-chart.md).  
  
## ¿Qué desea hacer?  
 *Utilice el archivo C*  
  
-   [Abra un archivo con CFile](../mfc/opening-files.md)  
  
-   [Leer y escribir un archivo con CFile](../mfc/reading-and-writing-files.md)  
  
-   [Cerrar un archivo con CFile](../mfc/closing-files.md)  
  
-   [Estado de archivo Access con CFile](../mfc/accessing-file-status.md)  
  
 *Serialización de MFC \(\/md persistencia de objeto\)*  
  
-   [Cree una clase serializable](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Serialice un objeto mediante un objeto CArchive](../mfc/serialization-serializing-an-object.md)  
  
-   [Cree un objeto CArchive](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [Utilice CArchive \<\< y \>\> operadores](../mfc/using-the-carchive-output-and-input-operators.md)  
  
-   [Almacenar y cargue CObjects y los objetos CObject\- derivados mediante un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [Cómo se hago: Utilice la clase de CFile?](http://go.microsoft.com/fwlink/?LinkId=128046)