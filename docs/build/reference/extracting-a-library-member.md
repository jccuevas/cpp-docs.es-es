---
title: "Extraer un miembro de biblioteca | Microsoft Docs"
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
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXTRACT (opción del administrador de bibliotecas)"
  - "EXTRACT (opción del administrador de bibliotecas)"
  - "-EXTRACT (opción del administrador de bibliotecas)"
  - "extraer miembros de biblioteca"
  - "LIB [C++], extraer miembros de biblioteca"
  - "bibliotecas, extraer miembros"
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Extraer un miembro de biblioteca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar LIB para crear un archivo objeto \(.obj\) que contenga una copia de un miembro de una biblioteca existente.  Para extraer una copia de un miembro, utilice la sintaxis siguiente:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 Este comando crea un archivo .obj denominado *objectfile*, que contiene una copia de un miembro \(`member`\) de una biblioteca \(*library*\).  Para el nombre del miembro se distingue mayúsculas de minúsculas.  Sólo puede extraer un miembro en cada comando.  La opción \/OUT es obligatoria; no hay un nombre de salida predeterminado.  Si ya existe un archivo denominado *objectfile* en el directorio especificado \(o en el directorio actual, si no se especifica ningún directorio con *objectfile*\), el archivo *objectfile* extraído reemplazará el archivo existente.  
  
## Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)