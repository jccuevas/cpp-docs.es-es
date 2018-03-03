---
title: C3173 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3173
dev_langs:
- C++
helpviewer_keywords:
- C3173
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e2cb965955cc172426ca5d94b8c41c89be23aba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3173"></a>C3173 de Error del compilador
Error de coincidencia de versión en la combinación de idl  
  
 Este error se produce cuando un archivo objeto contiene código idl incrustado que se generó con una versión anterior del compilador. El compilador codifica un número de versión para asegurarse de que el compilador usado para generar el contenido idl que se incrusta en los archivos .obj también es el mismo compilador que se usa para combinar el idl incrustado.  
  
 Actualizar la instalación de Visual C++ para que todas las herramientas tengan la versión más reciente.