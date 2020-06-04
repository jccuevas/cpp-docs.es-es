---
title: Creación de scripts para el registrador de ATL
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707059"
---
# <a name="creating-registrar-scripts"></a>Creación de scripts de registrador

Un script de registrador proporciona acceso controlado por datos, en lugar de controlado por la API, al registro del sistema. Normalmente, el acceso controlado por datos es más eficaz ya que solo se necesitan una o dos líneas en un script para agregar una clave al registro.

El [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera de forma automática un script de registrador para el servidor COM. Puede encontrar este script en el archivo .rgs asociado al objeto.

El Motor de scripts del registrador de ATL procesa el script de registrador en tiempo de ejecución. ATL invoca de forma automática el motor de scripts durante la instalación del servidor.

En este artículo se describen los temas siguientes relacionados con los scripts de registrador:

- [Conceptos sobre la sintaxis de forma de Backus-Naur (BNF)](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [Comprender los árboles de análisis](../atl/understanding-parse-trees.md)

- [Ejemplos de scripting del registro](../atl/registry-scripting-examples.md)

- [Usar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Invocar scripts](../atl/invoking-scripts.md)

## <a name="see-also"></a>Vea también

[Componente de registro (Registrador)](../atl/atl-registry-component-registrar.md)
