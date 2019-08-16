---
title: Error PRJ0002 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: d8e13bcc03a02fd9dbc739566a92025a7b97d598
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359714"
---
# <a name="project-build-error-prj0002"></a>Error PRJ0002 al compilar el proyecto

> resultado del error devuelto desde '*línea de comandos*'.

Un comando, *línea de comandos*, que estaba formada por el usuario en el **páginas de propiedades** aparecerá el cuadro de diálogo, devuelve un código de error, pero no hay información en el **salida** ventana .

La solución a este error depende de la herramienta que generó el error. Para MIDL, obtendrá una idea de qué salió mal si se define /o (Redirigir resultados).

Un archivo por lotes, por ejemplo, un paso de compilación personalizada o un evento de compilación que no es informativa sobre las condiciones de error también podría ser la causa de este error.