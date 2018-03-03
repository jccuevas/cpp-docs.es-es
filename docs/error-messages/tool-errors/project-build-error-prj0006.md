---
title: Error PRJ0006 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 817450fb6b72f985d7ff49f7e65f9dfa0933b4d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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