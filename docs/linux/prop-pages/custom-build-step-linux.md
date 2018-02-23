---
title: "Propiedades de paso de compilación personalizada (C++ para Linux) | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: b46ee18fce79c0e1954d37a87f6380c73870fa12
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="custom-build-step-properties-linux-c"></a>Propiedades de paso de compilación personalizada (C++ para Linux)

Property | Description
--- | ---
Línea de comandos | Comando que va a ejecutar el paso de compilación personalizada.
Description | Mensaje que se muestra cuando se ejecuta el paso de compilación personalizada.
Salidas | Archivo de salida que genera el paso de compilación personalizada. Este valor es necesario para que las compilaciones incrementales funcionen correctamente.
Dependencias adicionales | Lista delimitada por puntos y coma de los archivos de entrada adicionales que se usarán para el paso de compilación personalizada.
Ejecutar después y Ejecutar antes | Estas opciones definen cuándo se ejecuta el paso de compilación personalizada en el proceso de compilación, en relación con los destinos enumerados. Los destinos más frecuentes son BuildGenerateSources, BuildCompile y BuildLink, ya que representan los pasos principales del proceso de compilación. Otros destinos frecuentes son Midl, CLCompile y Link.
Tratar salida como contenido | Esta opción solo es significativa para las aplicaciones de Microsoft Store o Windows Phone, que incluyen todos los archivos de contenido en el paquete .appx.