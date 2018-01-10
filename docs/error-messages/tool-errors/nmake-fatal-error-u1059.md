---
title: Error grave de NMAKE U1059 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1059
dev_langs: C++
helpviewer_keywords: U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb9ba98b0f82c158e4e11859e85af72efdbbc244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059
error de sintaxis: '}' falta en dependientes  
  
 Se especificó incorrectamente una ruta de acceso de búsqueda para un dependiente. Existe un espacio en la ruta de acceso o la llave de cierre (**}**) se ha omitido.  
  
 La sintaxis para una especificación de directorio para un dependiente es  
  
 **{**   
 ***directorios* } dependientes**  
  
 donde `directories` especifica una o varias rutas, separados por un punto y coma (**;**). No se permiten espacios.  
  
 Si parte o la totalidad de una ruta de acceso de búsqueda se sustituye por una macro, asegúrese de que no existan espacios en la expansión de macro.