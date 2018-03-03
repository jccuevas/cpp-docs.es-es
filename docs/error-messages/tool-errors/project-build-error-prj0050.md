---
title: Error PRJ0050 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9d9b123da2e32db0f695c31bc9643a481d352b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0050"></a>Error PRJ0050 al compilar el proyecto
No se pudo registrar la salida. Asegúrese de que tiene los permisos adecuados para modificar el registro.  
  
 El sistema de compilación de Visual C++ no pudo registrar la salida de la compilación (archivo dll o .exe). Debe haber iniciado sesión como administrador para modificar el registro.  
  
 Si está generando un archivo .dll, puede intentar registrar el archivo .dll manualmente mediante regsvr32.exe, debería mostrarse información sobre por qué falló la compilación.  
  
 Si no se genera un archivo .dll, examine el registro de compilación para el comando que se produzca un error.