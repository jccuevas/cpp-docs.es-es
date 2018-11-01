---
title: Eventos de compilación remota (C++ para Linux) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 2ea01c5d92cbdb6066dc87675221eae6865af354
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070990"
---
# <a name="build-event-properties-linux-c"></a>Propiedades de evento de compilación (C++ para Linux)

## <a name="pre-build-event"></a>Evento anterior a la compilación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos anteriores a la compilación.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la compilación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.

## <a name="pre-link-event"></a>Evento anterior a la vinculación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos anteriores a la vinculación.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la vinculación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.

## <a name="post-build-event"></a>Evento posterior a la compilación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos posteriores a la compilación.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos posteriores a la compilación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.

## <a name="remote-pre-build-event"></a>Evento remoto anterior a la compilación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos anteriores a la compilación en el sistema remoto.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la compilación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de remoto a local usando la sintaxis siguiente: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada de la máquina local.

## <a name="remote-pre-link-event"></a>Evento remoto anterior a la vinculación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos previos a la vinculación en el sistema remoto.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la vinculación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de remoto a local usando la sintaxis siguiente: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada de la máquina local.

## <a name="remote-post-build-event"></a>Evento remoto posterior a la compilación

Propiedad. | Descripción
--- | ---
Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos posteriores a la compilación en el sistema remoto.
Descripción | Especifica una descripción que se mostrará para la herramienta de eventos posteriores a la compilación.
Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual.
Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de remoto a local usando la sintaxis siguiente: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada de la máquina local.
