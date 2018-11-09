---
title: Propiedades de paso de compilación personalizada (C++ para Linux)
ms.date: 10/17/2017
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 5e6580263e63547e3564eaee260158a312e5fa6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644709"
---
# <a name="custom-build-step-properties-linux-c"></a>Propiedades de paso de compilación personalizada (C++ para Linux)

Propiedad. | Descripción
--- | ---
Línea de comandos | Comando que va a ejecutar el paso de compilación personalizada.
Descripción | Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada.
Salidas | Archivo de salida que genera el paso de compilación personalizada. Este valor es necesario para que las compilaciones incrementales funcionen correctamente.
Dependencias adicionales | Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada.
Ejecutar después y Ejecutar antes | Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados. Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación. Otros destinos frecuentes son Midl, CLCompile y Link.
Tratar salida como contenido | Esta opción solo es significativa para las aplicaciones de Microsoft Store o Windows Phone, que incluyen todos los archivos de contenido en el paquete .appx.