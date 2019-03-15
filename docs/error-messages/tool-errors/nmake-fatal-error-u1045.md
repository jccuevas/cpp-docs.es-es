---
title: Error grave de NMAKE U1045
ms.date: 11/04/2016
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: 0937e83303fefdf1f2aaaa5eea6f43c27159fd57
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808240"
---
# <a name="nmake-fatal-error-u1045"></a>Error grave de NMAKE U1045

error al generar: mensaje

Error por la razón indicada en un programa o un comando llamado por NMAKE. Cuando NMAKE llama a otro programa (por ejemplo, el compilador o el vinculador), puede producirse un error en la llamada, o el programa llamado puede devolver un error. Este mensaje se utiliza para informar sobre el error.

Para corregir este problema, primero hay que determinar la causa del error. Puede usar los comandos registrados por el NMAKE [/N](../../build/reference/nmake-options.md) opción para comprobar la configuración del entorno y repetir las acciones realizadas por NMAKE en la línea de comandos.