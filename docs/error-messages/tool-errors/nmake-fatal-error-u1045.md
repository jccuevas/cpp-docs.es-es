---
title: Error grave de NMAKE U1045 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 673b20dde7156025c6aa56c487433eebe9e77aa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1045"></a>Error grave de NMAKE U1045
error al generar: mensaje  
  
 Error por la razón indicada en un programa o un comando llamado por NMAKE. Cuando NMAKE llama a otro programa (por ejemplo, el compilador o el vinculador), puede producirse un error en la llamada, o el programa llamado puede devolver un error. Este mensaje se utiliza para informar sobre el error.  
  
 Para corregir este problema, primero hay que determinar la causa del error. Puede utilizar los comandos registrados por el NMAKE [/N](../../build/nmake-options.md) opción para comprobar la configuración del entorno y repetir las acciones realizadas por NMAKE en la línea de comandos.