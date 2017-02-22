---
title: "Abrir archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFile (clase), variable"
  - "ejemplos [MFC], abrir archivos"
  - "control de excepciones [C++], abrir archivos"
  - "control de excepciones [C++], cuándo abrir archivos"
  - "file (objetos) [C++]"
  - "archivos [C++], abrir"
  - "MFC [C++], operaciones en archivo"
  - "llamadas Open"
  - "funciones de miembro Open"
  - "Open (método), CFile (clase)"
  - "abrir archivos"
  - "abrir archivos, controlar excepciones"
  - "abrir archivos, en MFC"
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Abrir archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En MFC, la manera más común de abrir un archivo es un proceso de dos pasos.  
  
#### Para abrir un archivo  
  
1.  Cree el objeto de archivo sin especificar una ruta de acceso o marcadores de permiso.  
  
     Se suele crear un objeto de archivo declarar una variable de [Archivo C](../mfc/reference/cfile-class.md) en el marco de pila.  
  
2.  Llame a la función miembro de [Abierta](../Topic/CFile::Open.md) para el objeto de archivo, proporcionando una ruta y marcadores de permiso.  
  
     El valor devuelto para `Open` será distinto de cero si el archivo se ha abierto correctamente o 0 si el archivo especificado no puede estar abierto.  La función miembro de `Open` es prototipo como sigue:  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     Los indicadores abierto especifican que los permisos, como de sólo lectura, desea el archivo.  Los valores posibles de marcador se definen como constantes que aparece dentro de la clase de `CFile` , por lo que se califican con “`CFile::`” como en `CFile::modeRead`.  Utilice el marcador de `CFile::modeCreate` si desea crear el archivo.  
  
 El ejemplo siguiente muestra cómo crear un nuevo archivo con permisos de lectura y escritura \(que reemplaza cualquier archivo anterior con la misma ruta\):  
  
 [!code-cpp[NVC_MFCFiles#1](../mfc/codesnippet/CPP/opening-files_1.cpp)]  
  
> [!NOTE]
>  Este ejemplo crea y abre un archivo.  Si hay problemas, la llamada de `Open` puede devolver un objeto de `CFileException` en su último parámetro, como se muestra aquí.  La macro de `TRACE` imprime el nombre de archivo y un código que indican la razón del error.  Puede llamar a la función de `AfxThrowFileException` si requiere un informe de error más detallado.  
  
## Vea también  
 [CFile Class](../mfc/reference/cfile-class.md)   
 [CFile::Open](../Topic/CFile::Open.md)   
 [Archivos](../mfc/files-in-mfc.md)