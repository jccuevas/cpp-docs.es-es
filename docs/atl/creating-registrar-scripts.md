---
title: Crear Scripts para el registrador de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: e1a0b66e673fcefd0b75683ef75247a388217361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250858"
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
