---
title: Error del compilador de recursos RC2104 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC2104
dev_langs:
- C++
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce7fa189e03ec907c4b42f381096f095d5df734a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2104"></a>Error del compilador de recursos RC2104
palabra clave o nombre de clave sin definir: clave  
  
 La palabra clave o el nombre de clave especificados no se ha definido.  
  
 A menudo, este error se debe a un error de escritura en la definición del recurso o en el archivo de encabezado incluido. También puede deberse a que falta un archivo de encabezado.  
  
 Para corregir el problema, busque el archivo de encabezado que debe contener la palabra clave o el nombre de clave definidos y compruebe que se han incluido en el archivo de recursos, y que la palabra clave o el nombre de clave están escritos correctamente. Si el proyecto se creó con un encabezado precompilado y posteriormente lo eliminó, asegúrese de que el archivo de recursos sigue incluyendo los encabezados necesarios.  
  
 Para comprobar las palabras clave definidas y nombres de clave en el archivo de recursos, en Visual Studio, abra el **vista de recursos** ventana, en la barra de menús, elija **vista**, **vista de recursos**: y a continuación, abra el menú contextual para el archivo .rc y elija **símbolos de recursos** para ver la lista de símbolos definidos. Para modificar los encabezados incluidos, abra el menú contextual para el archivo .rc y elija **de inclusión de recursos**.  
  
 Si aparece este mensaje:  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 abra \MCL\MFC\Include\AfxRes.h y agregue esta directiva Include:  
  
```  
#include <winresrc.h>  
```