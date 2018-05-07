---
title: Error grave de NMAKE U1059 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059
error de sintaxis: '}' falta en dependientes  
  
 Se especificó incorrectamente una ruta de acceso de búsqueda para un dependiente. Existe un espacio en la ruta de acceso o la llave de cierre (**}**) se ha omitido.  
  
 La sintaxis para una especificación de directorio para un dependiente es  
  
 **{**   
 ***directorios* } dependientes**  
  
 donde `directories` especifica una o varias rutas, separados por un punto y coma (**;**). No se permiten espacios.  
  
 Si parte o la totalidad de una ruta de acceso de búsqueda se sustituye por una macro, asegúrese de que no existan espacios en la expansión de macro.