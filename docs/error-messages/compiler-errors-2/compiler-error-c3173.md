---
title: Error del compilador C3173 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3173
dev_langs:
- C++
helpviewer_keywords:
- C3173
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a02ae1fcf4aff9636445979a81ef0a02ab5cb1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053029"
---
# <a name="compiler-error-c3173"></a>Error del compilador C3173

Error de coincidencia de versión en la combinación de idl

Este error se produce cuando un archivo objeto contiene idl incrustado que se generó con una versión anterior del compilador. El compilador codifica un número de versión para asegurarse de que el compilador usado para generar el contenido de idl incrustado en los archivos .obj también es el mismo compilador utilizado para combinar el idl incrustado.

Actualizar la instalación de Visual C++ para que todas las herramientas son de la versión más reciente.