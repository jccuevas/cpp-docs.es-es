---
title: Error PRJ0030 al compilar del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf1c9137f8c4ed0d80955eef38b07ea86204a5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto
Error de expansión de macro. Evaluar recursividad superado 32 niveles para $(macro).  
  
 Este error se produce por recursividad en las macros. Por ejemplo, si establece la **directorio intermedio** propiedad (vea [página de propiedades General (proyecto)](../../ide/general-property-page-project.md)) en $(IntDir), se obtendrá recursividad.  
  
 Para resolver este error, no defina macros ni propiedades en cuanto a las macros que se utilizan para definir.