---
title: Eventos de compilación remota (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441498"
---
# <a name="build-event-properties-linux-c"></a>Propiedades de evento de compilación (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Evento anterior a la compilación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos anteriores a la compilación. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la compilación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se pueden especificar pares de asignación de local a remoto con esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada en el sistema remoto. |

## <a name="pre-link-event"></a>Evento anterior a la vinculación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos anteriores a la vinculación. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la vinculación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se pueden especificar pares de asignación de local a remoto con esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada en el sistema remoto. |

## <a name="post-build-event"></a>Evento posterior a la compilación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para ejecutar la herramienta de eventos posteriores a la compilación. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos posteriores a la compilación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales para copiar en el sistema remoto. También se pueden especificar pares de asignación de local a remoto con esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada en el sistema remoto. |

## <a name="remote-pre-build-event"></a>Evento remoto anterior a la compilación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos anteriores a la compilación en el sistema remoto. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la compilación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se pueden especificar pares de asignación de remoto a local con esta sintaxis: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada en la máquina local. |

## <a name="remote-pre-link-event"></a>Evento remoto anterior a la vinculación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos previos a la vinculación en el sistema remoto. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos anteriores a la vinculación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se pueden especificar pares de asignación de remoto a local con esta sintaxis: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada en la máquina local. |

## <a name="remote-post-build-event"></a>Evento remoto posterior a la compilación

| Propiedad. | Descripción |
|--|--|
| Línea de comandos | Especifica una línea de comandos para que la ejecute la herramienta de eventos posteriores a la compilación en el sistema remoto. |
| Descripción | Especifica una descripción que se mostrará para la herramienta de eventos posteriores a la compilación. |
| Usar en la compilación | Especifica si este evento de compilación se excluirá de la compilación en la configuración actual. |
| Archivos adicionales para copiar | Especifica archivos adicionales que se copiarán del sistema remoto. También se pueden especificar pares de asignación de remoto a local con esta sintaxis: rutaDeAccesoRemotaCompleta1:=rutaDeAccesoLocalCompleta1;rutaDeAccesoRemotaCompleta2:=rutaDeAccesoLocalCompleta2, donde un archivo remoto se puede copiar en la ubicación especificada en la máquina local. |

::: moniker-end
