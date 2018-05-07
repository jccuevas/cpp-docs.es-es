---
title: Las herramientas del vinculador LNK4092 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4092"></a>Advertencia de las herramientas del vinculador LNK4092
la sección 'sección' compartida modificable contiene reubicaciones; Puede que la imagen no se ejecute correctamente  
  
 El vinculador emite esta advertencia siempre que tenga una sección compartida para avisarle de un problema potencialmente grave.  
  
 Es una manera de compartir datos entre varios procesos marcar una sección como "compartido". Sin embargo, al marcar una sección como compartida puede causar problemas. Por ejemplo, tiene un archivo DLL que contiene declaraciones como ésta en una sección de datos compartidos:  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 No se puede resolver el vinculador `pvar` porque su valor depende de dónde se carga el archivo DLL en la memoria, por lo que inserta un registro de reubicación en la DLL. Cuando se carga el archivo DLL en la memoria, la dirección de `var` se puede resolver y `pvar` asignado. Si otro proceso carga la misma DLL pero no puede cargarla en la misma dirección, la reubicación de la dirección de `var` se actualizará para el segundo proceso y espacio de direcciones del primer proceso apuntará a la dirección equivocada.