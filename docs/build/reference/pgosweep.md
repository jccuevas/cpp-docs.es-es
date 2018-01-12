---
title: PGOSWEEP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78ae6c36011e3c10359988cf2c501514d1bcf70a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pgosweep"></a>pgosweep
Se usan en optimización guiada por perfiles para escribir todos los datos de perfil de un programa en ejecución en el archivo .pgc.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### <a name="parameters"></a>Parámetros  
 `options`  
 Un parámetro opcional que puede dejarse en blanco. Los valores válidos para `options` son los siguientes:  
  
-   **/?** o **/Help,** muestra el mensaje de ayuda.  
  
-   **/ NoReset,** conserva el recuento de las estructuras de datos en tiempo de ejecución.  
  
 `image`  
 La ruta de acceso completa de un archivo .exe o .dll que se creó mediante la opción de compilador/LTCG: PGINSTRUMENT.  
  
 `pgcfile`  
 El archivo .pgc donde este comando escribirá los datos de recuentos.  
  
## <a name="remarks"></a>Comentarios  
 Este comando funciona en programas que se crearon con la opción del compilador/LTCG: PGINSTRUMENT. Interrumpe un programa en ejecución y escribe los datos de perfil en un nuevo archivo .pgc. De forma predeterminada, el comando restablece los recuentos después de cada operación de escritura. Si especifica la **/NoReset** opción, el comando registrar los valores, pero no restablecerlas en el programa en ejecución. Esta opción le proporcionará los datos duplicados si se recuperan los datos de perfil más adelante.  
  
 Un uso alternativo para `pgosweep` consiste en recuperar información del perfil para el tiempo de ejecución de la aplicación. Por ejemplo, podría ejecutar `pgosweep` poco después de iniciar la aplicación y descartar ese archivo. Esto quitará los datos de perfil asociados a los costos de inicio. A continuación, puede ejecutar `pgosweep` antes de finalizar la aplicación. Ahora los datos recopilados tienen información de perfil sólo de tiempo de ejecución.  
  
 Cuando asigne un nombre a un archivo .pgc (`pgcfile`) puede usar el formato estándar, que es *appname! n*.pgc. Si utiliza este formato, el compilador buscará estos datos en la fase/LTCG: PGO. Si no utiliza el formato estándar, debe usar [pgomgr](../../build/reference/pgomgr.md) para combinar los archivos .pgc que existan.  
  
## <a name="example"></a>Ejemplo  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 En este ejemplo, `pgosweep` escribe la información de perfil actual para myapp.exe en 1.pgc.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas para la optimización manual guiada por perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)