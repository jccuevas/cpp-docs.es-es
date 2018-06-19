---
title: Compilador advertencia (nivel 1) C4819 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718e0783c3f7afcc9af958f7940f437ac4c944b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283385"
---
# <a name="compiler-warning-level-1-c4819"></a>Advertencia del compilador (nivel 1) C4819
El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guarde el archivo en formato Unicode para evitar la pérdida de datos.  
  
 C4819 se produce cuando un archivo de código fuente ANSI se compila en un sistema con una página de códigos que no puede representar todos los caracteres del archivo.  
  
 Para resolver C4819, guarde el archivo en formato Unicode. En Visual Studio, elija **archivo**, **opciones avanzadas para guardar**. En el **opciones avanzadas para guardar** cuadro de diálogo, seleccione una codificación que puede representar todos los caracteres en el archivo, por ejemplo, UTF-8 y, a continuación, elija **Aceptar**.