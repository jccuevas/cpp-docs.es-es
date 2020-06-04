---
title: Propiedades de paso de compilación personalizada (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 67b281e245c4fff8f37baff8875cbc3dc84ca718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441333"
---
# <a name="custom-build-step-properties-linux-c"></a>Propiedades de paso de compilación personalizada (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Comando que va a ejecutar el paso de compilación personalizada. |
| Descripción | Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada. |
| Salidas | Archivo de salida que genera el paso de compilación personalizada. Este valor es necesario para que las compilaciones incrementales funcionen correctamente. |
| Dependencias adicionales | Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada. |
| Ejecutar después y Ejecutar antes | Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados. Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación. Otros destinos frecuentes son Midl, CLCompile y Link. |
| Tratar salida como contenido | Esta opción solo es significativa para las aplicaciones de Microsoft Store o Windows Phone, que incluyen todos los archivos de contenido en el paquete .appx. |

::: moniker-end
