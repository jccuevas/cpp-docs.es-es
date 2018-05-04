---
title: Crear Scripts para el registrador de ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e140e66ee24d8333d25c0c2942924c7a9db4965b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts
Una secuencia de comandos del registrador proporciona controladas por datos, en lugar de controlada por la API, acceso al registro del sistema. Acceso controlada por datos es normalmente más eficaz ya que toma solo una o dos líneas en una secuencia de comandos para agregar una clave al registro.  
  
 El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera automáticamente una secuencia de comandos del registrador para el servidor COM. Puede encontrar esta secuencia de comandos en el archivo .rgs asociado al objeto.  
  
 Motor de scripts del registrador de ATL procesa la secuencia de comandos del registrador en tiempo de ejecución. ATL invoca automáticamente el motor de scripts durante la instalación de servidor.  
  
 En este artículo se trata los siguientes temas relacionados con los scripts del registrador:  
  
-   [Comprender la sintaxis de Backus Nauer Form (BNF)](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [Comprender los árboles de análisis](../atl/understanding-parse-trees.md)  
  
-   [Ejemplos de scripting del registro](../atl/registry-scripting-examples.md)  
  
-   [Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [Invocar scripts](../atl/invoking-scripts.md)  
  
## <a name="see-also"></a>Vea también  
 [Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)

