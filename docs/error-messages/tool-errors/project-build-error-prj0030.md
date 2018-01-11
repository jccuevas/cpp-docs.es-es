---
title: Error PRJ0030 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0030
dev_langs: C++
helpviewer_keywords: PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6fe537dd8e6705fd5e30929a2480eb1d9ef9119
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto
Error de expansión de macro. Evaluar recursividad superado 32 niveles para $(macro).  
  
 Este error se produce por recursividad en las macros. Por ejemplo, si establece la **directorio intermedio** propiedad (vea [página de propiedades General (proyecto)](../../ide/general-property-page-project.md)) en $(IntDir), se obtendrá recursividad.  
  
 Para resolver este error, no defina macros ni propiedades en cuanto a las macros que se utilizan para definir.