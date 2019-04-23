---
title: Advertencia del compilador (nivel 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777844"
---
# <a name="compiler-warning-level-1-c4819"></a>Advertencia del compilador (nivel 1) C4819

> El archivo contiene un carácter que no se puede representar en la página de códigos actual (*número*). Guarde el archivo en formato Unicode para evitar la pérdida de datos.

C4819 se produce cuando se compila un archivo de código fuente ANSI en un sistema con una página de códigos que no se puede representar todos los caracteres en el archivo.

Hay varias maneras de resolver C4819. Es una forma sencilla de quitar el carácter incorrecto, si no necesita, por ejemplo, si se encuentra en un comentario. Puede establecer la página de códigos del sistema en el Panel de Control a una que admita el juego de caracteres utilizado por el código fuente. Puede utilizar Unicode [secuencias de escape](/cpp/c-language/escape-sequences) para crear caracteres o cadenas que usan ANSI básica juego de caracteres de en el código fuente. Por último, puede guardar el archivo en formato Unicode con una firma, también conocido como una marca de orden de bytes (BOM).

Para guardar un archivo en formato Unicode, en Visual Studio, elija **archivo** > **Guardar como**. En el **Guardar archivo como** cuadro de diálogo, seleccione la lista desplegable en el **guardar** botón y elija **guardar con codificación**. Si lo guarda en el mismo nombre de archivo, deberá confirmar que desea reemplazar el archivo. En el **opciones avanzadas para guardar** cuadro de diálogo, elija una codificación que puede representar todos los caracteres en el archivo, por ejemplo, **Unicode (UTF-8 con firma) - página de códigos 65001**— y, a continuación, elija  **Aceptar**.