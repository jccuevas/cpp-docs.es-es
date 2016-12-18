---
title: "C&#243;mo: Combinar varios perfiles PGO en un solo perfil | Microsoft Docs"
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
  - "combinar perfiles"
  - "optimizaciones guiadas por perfiles, combinar perfiles"
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Combinar varios perfiles PGO en un solo perfil
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La optimización guiada por perfiles \(PGO\) es una gran herramienta para crear archivos binarios optimizados basados en un escenario del que se genera un perfil.  Pero qué ocurre si dispone de una aplicación que tiene varios escenarios importantes pero distintos; cómo crearía un único perfil que PGO pueda usar a partir de varios escenarios diferentes.  En Visual Studio, es el Administrador PGO, Pgomgr.exe, el que realiza este trabajo.  
  
 La sintaxis para combinar perfiles es:  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 donde `num` es un peso opcional que se utiliza para esta combinación.  Los pesos se utilizan habitualmente si hay algún escenario más importante que otro, o si existen escenarios que se tienen que ejecutar varias veces.  
  
> [!NOTE]
>  El Administrador PGO no funcionará con datos de perfil obsoletos.  Para combinar un archivo .pgc en un archivo .pgd, el archivo .pgc lo debe generar un ejecutable creado por la misma invocación de vínculo que generó el archivo .pgd.  
  
## Ejemplo  
 En este ejemplo, el Administrador PGO agregará pgcFile.pgc a pgdFile.pgd seis veces.  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## Ejemplo  
 En este ejemplo, el Administrador PGO agregará pgcFile1.pgc y pgcFile2.pgc a pgdFile.pgd, dos veces para cada archivo .pgc.  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## Ejemplo  
 Si el Administrador PGO se ejecuta sin archivo .pgc, buscará en el directorio local todos los archivos .pgc que tengan el mismo nombre que el archivo .pgd anexado con un signo de admiración \(\!\) seguido de caracteres arbitrarios.  Si el directorio local tiene los archivos test.pgd, test\!1.pgc, test2.pgc y test\!hello.pgc, y se ejecuta el siguiente comando desde el directorio local, entonces test\!1.pgc y test\!hello.pgc se combinarán en el archivo test.pgd.  
  
```  
pgomgr /merge test.pgd  
```  
  
## Vea también  
 [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)