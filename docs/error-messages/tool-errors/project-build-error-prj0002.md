---
title: Error PRJ0002 al compilar el proyecto
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: 30680f5b26f3be5e7f9b48d18e82fca42ed65493
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192944"
---
# <a name="project-build-error-prj0002"></a>Error PRJ0002 al compilar el proyecto

> resultado de error devuelto desde '*línea de comandos*'.

Un comando, *línea de comandos*, que se formó a partir de los datos proporcionados por el usuario en el cuadro de diálogo **páginas de propiedades** , devolvió un código de error pero no aparece ninguna información en la ventana de **salida** .

La resolución de este error depende de la herramienta que ha generado el error. Para MIDL, obtendrá una idea de lo que ha ido mal si se define/o (redirigir la salida).

Un archivo por lotes, como un paso de compilación personalizada o un evento de compilación, que no es informativo sobre las condiciones de error también podría ser el motivo de este error.
