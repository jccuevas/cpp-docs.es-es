---
title: C3173 de Error del compilador | Documentos de Microsoft
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
ms.openlocfilehash: ef35c534ac834779da15fce99e8c82b94bd445e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3173"></a>C3173 de Error del compilador
Error de coincidencia de versión en la combinación de idl  
  
 Este error se produce cuando un archivo objeto contiene código idl incrustado que se generó con una versión anterior del compilador. El compilador codifica un número de versión para asegurarse de que el compilador usado para generar el contenido idl que se incrusta en los archivos .obj también es el mismo compilador que se usa para combinar el idl incrustado.  
  
 Actualizar la instalación de Visual C++ para que todas las herramientas tengan la versión más reciente.