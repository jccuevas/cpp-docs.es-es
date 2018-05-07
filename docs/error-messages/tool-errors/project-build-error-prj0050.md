---
title: Error PRJ0050 al compilar del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad17614f693e313190dba9cc767c023981dec34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0050"></a>Error PRJ0050 al compilar el proyecto
No se pudo registrar la salida. Asegúrese de que tiene los permisos adecuados para modificar el registro.  
  
 El sistema de compilación de Visual C++ no pudo registrar la salida de la compilación (archivo dll o .exe). Debe haber iniciado sesión como administrador para modificar el registro.  
  
 Si está generando un archivo .dll, puede intentar registrar el archivo .dll manualmente mediante regsvr32.exe, debería mostrarse información sobre por qué falló la compilación.  
  
 Si no se genera un archivo .dll, examine el registro de compilación para el comando que se produzca un error.