---
title: Error PRJ0002 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195720"
---
# <a name="project-build-error-prj0002"></a>Error PRJ0002 al compilar el proyecto

> resultado del error devuelto desde '*línea de comandos*'.

Un comando, *línea de comandos*, que estaba formada por el usuario en el **páginas de propiedades** aparecerá el cuadro de diálogo, devuelve un código de error, pero no hay información en el **salida** ventana .

La solución a este error depende de la herramienta que generó el error. Para MIDL, obtendrá una idea de qué salió mal si se define /o (Redirigir resultados).

Un archivo por lotes, por ejemplo, un paso de compilación personalizada o un evento de compilación que no es informativa sobre las condiciones de error también podría ser la causa de este error.