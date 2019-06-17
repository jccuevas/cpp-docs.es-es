---
title: Eventos de compilación remota (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 1e5c453da05fe65871fa7f6b0d4ca6528a96d4dd
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821480"
---
# <a name="build-event-properties-linux-c"></a>Propiedades de evento de compilación (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

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

::: moniker-end


