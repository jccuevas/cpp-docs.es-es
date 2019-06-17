---
title: Propiedades del proyecto Copiar orígenes (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: afc65fb7fbc3866081fbf7da6d3c5014ba1c268d
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821325"
---
# <a name="copy-sources-project-properties-linux-c"></a>Propiedades del proyecto Copiar orígenes (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Las propiedades establecidas en esta página de propiedades se aplican a todos los archivos del proyecto, excepto a aquellos cuyas propiedades de nivel de archivo están establecidas.

Propiedad. | Descripción
--- | ---
Orígenes para copiar | Especifica los orígenes que deben copiarse en el sistema remoto. Si se cambia esta lista, podría modificar o afectar de alguna manera a la estructura de directorios donde se copian los archivos en el sistema remoto.
Copiar orígenes | Especifica si deben copiarse los orígenes en el sistema remoto.
Más orígenes para copiar | Especifica otros orígenes que deben copiarse en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.

::: moniker-end
