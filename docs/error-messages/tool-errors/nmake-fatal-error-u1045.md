---
title: Error grave de NMAKE U1045 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cdd9fb3d0bcee20e1952cea6444f586a9117365a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1045"></a>Error grave de NMAKE U1045
error al generar: mensaje  
  
 Error por la razón indicada en un programa o un comando llamado por NMAKE. Cuando NMAKE llama a otro programa (por ejemplo, el compilador o el vinculador), puede producirse un error en la llamada, o el programa llamado puede devolver un error. Este mensaje se utiliza para informar sobre el error.  
  
 Para corregir este problema, primero hay que determinar la causa del error. Puede utilizar los comandos registrados por el NMAKE [/N](../../build/nmake-options.md) opción para comprobar la configuración del entorno y repetir las acciones realizadas por NMAKE en la línea de comandos.