---
title: Advertencia del compilador (nivel 1) C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596617"
---
# <a name="compiler-warning-level-1-c4819"></a>Advertencia del compilador (nivel 1) C4819

El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guarde el archivo en formato Unicode para evitar la pérdida de datos.

C4819 se produce cuando un archivo de código fuente ANSI se compila en un sistema con una página de códigos que no puede representar todos los caracteres del archivo.

Para resolver C4819, guarde el archivo en formato Unicode. En Visual Studio, elija **archivo**, **opciones avanzadas para guardar**. En el **opciones avanzadas para guardar** cuadro de diálogo, seleccione una codificación que puede representar todos los caracteres en el archivo, por ejemplo, UTF-8 y, a continuación, elija **Aceptar**.