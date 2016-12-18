---
title: "Error PRJ0006 al compilar el proyecto | Microsoft Docs"
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
  - "PRJ0006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0006"
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0006 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede abrir el archivo temporal 'nombre\_archivo'.Compruebe que el archivo existe y que el directorio no está protegido contra escritura.  
  
 Visual C\+\+ no pudo crear un archivo temporal durante el proceso de generación.  Las razones posibles son:  
  
-   No hay un directorio temp.  
  
-   El directorio temp es de sólo lectura.  
  
-   No hay suficiente espacio en disco.  
  
-   La carpeta $\(IntDir\) es de sólo lectura o contiene archivos temporales que son de sólo lectura.  
  
 Este error también se producirá a continuación del error PRJ0007: No se puede crear el directorio de resultados 'directorio'.  El error PRJ0007 indica que no se ha podido crear el directorio $\(IntDir\), lo que implica que tampoco se podrán crear archivos temporales.  
  
 Se crearán archivos temporales siempre que especifique:  
  
-   Un archivo de respuesta.  
  
-   Un paso de compilación personalizada.  
  
-   Un evento de compilación.