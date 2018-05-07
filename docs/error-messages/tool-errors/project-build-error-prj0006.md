---
title: Error PRJ0006 al compilar del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151c22bf13c13de21e89a5c96185cf1c4c1ca349
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0006"></a>Error PRJ0006 al compilar el proyecto
No se pudo abrir el archivo temporal 'archivo'. Asegúrese de que el archivo existe y que el directorio no está protegido contra escritura.  
  
 Visual C++ no se pudo crear un archivo temporal durante el proceso de compilación. Motivos pueden ser:  
  
-   Ningún directorio temporal.  
  
-   Directorio temporal de solo lectura.  
  
-   Espacio en disco.  
  
-   La carpeta $ (IntDir) es de solo lectura o contiene archivos temporales que son de solo lectura.  
  
 Este error también se producirá tras error PRJ0007: no se pudo crear el directorio de resultados 'directorio'. Error PRJ0007 al significa que no se pudo crear el directorio $ (IntDir), lo que implica la creación de archivos temporales se seguirán produciendo errores.  
  
 Archivos temporales se crean siempre que especifique:  
  
-   Un archivo de respuesta.  
  
-   Un paso de compilación personalizada.  
  
-   Un evento de compilación.