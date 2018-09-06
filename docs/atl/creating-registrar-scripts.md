---
title: Crear Scripts para el registrador de ATL | Microsoft Docs
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
ms.openlocfilehash: abffe3c8d0a107c48c3a14a9bf584122229ad3b7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767265"
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts

Un script de registrador proporciona acceso controlado por datos, en lugar de controlado por la API, el registro del sistema. Acceso controlado por datos es normalmente más eficaz ya que tarda sólo una o dos líneas en un script para agregar una clave al registro.

El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera automáticamente un script de registrador para el servidor COM. Puede encontrar esta secuencia de comandos en el archivo .rgs asociado al objeto.

Motor de scripts del registrador de ATL procesa el script de registrador en tiempo de ejecución. ATL invoca automáticamente el motor de scripts durante la instalación del servidor.

En este artículo se trata los siguientes temas relacionados con los scripts del registrador:

- [Comprender la sintaxis de Backus Nauer Form (BNF)](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [Comprender los árboles de análisis](../atl/understanding-parse-trees.md)

- [Ejemplos de scripting del registro](../atl/registry-scripting-examples.md)

- [Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Invocar scripts](../atl/invoking-scripts.md)

## <a name="see-also"></a>Vea también

[Componente de registro (registrador)](../atl/atl-registry-component-registrar.md)

