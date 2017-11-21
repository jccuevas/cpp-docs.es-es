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
ms.openlocfilehash: 70b1546068678c811f6123d3c8059dfd6d914f4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059
error de sintaxis: '}' falta en dependientes  
  
 Se especificó incorrectamente una ruta de acceso de búsqueda para un dependiente. Existe un espacio en la ruta de acceso o la llave de cierre (**}**) se ha omitido.  
  
 La sintaxis para una especificación de directorio para un dependiente es  
  
 **{**   
 ***directorios* } dependientes**  
  
 donde `directories` especifica una o varias rutas, separados por un punto y coma (**;**). No se permiten espacios.  
  
 Si parte o la totalidad de una ruta de acceso de búsqueda se sustituye por una macro, asegúrese de que no existan espacios en la expansión de macro.