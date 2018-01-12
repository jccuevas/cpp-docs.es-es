---
title: "Cómo: combinar varios perfiles PGO en un solo perfil | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 880e9fbba7852a9a7919e73f80b73e34394cd037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Cómo: Fusionar mediante combinación varios perfiles PGO en un solo perfil
Optimización guiada por perfiles (PGO) es una herramienta excelente para crear archivos binarios optimizados basados en un escenario que se generan los perfiles. Pero ¿qué ocurre si tiene una aplicación que tiene varios escenarios importantes, pero distintos; ¿cómo se crea un perfil único que puede utilizar PGO entre varios escenarios distintos? En Visual Studio, el Administrador PGO, Pgomgr.exe, realiza este trabajo automáticamente.  
  
 La sintaxis para combinar perfiles es:  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 donde `num` es un peso opcional que se utiliza para esta combinación. Pesos suelen usarse si no hay algunos escenarios que son más importantes que otros usuarios o si hay escenarios que van son ejecutarse varias veces.  
  
> [!NOTE]
>  El Administrador PGO no funcionará con datos de perfil obsoletos. Para combinar un archivo .pgc en un archivo .pgd, el archivo .pgc debe generarse mediante un archivo ejecutable que se creó por la misma invocación de vínculo que generó el archivo. pgd.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el Administrador PGO agregará pgcFile.pgc a pgdFile.pgd seis veces.  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el Administrador PGO agregará pgcFile1.pgc y pgcFile2.pgc a pgdFile.pgd, dos veces para cada archivo .pgc.  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Ejemplo  
 Si el Administrador PGO se ejecuta sin un archivo .pgc buscará el directorio local de todos los archivos .pgc que tengan el mismo nombre que el archivo .pgd anexado con un signo de admiración (!) seguido de caracteres arbitrarios. Si el directorio local tiene archivos test.pgd, Test! 1.pgc, test2.pgc y test! hello.pgc, y se ejecuta el siguiente comando desde el directorio local, Test! 1.pgc y test! hello.pgc se combinarán en el archivo test.pgd.  
  
```  
pgomgr /merge test.pgd  
```  
  
## <a name="see-also"></a>Vea también  
 [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)