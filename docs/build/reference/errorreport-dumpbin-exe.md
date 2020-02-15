---
title: /ERRORREPORT (dumpbin.exe)
description: Referencia de la opción de línea de comandos/ERRORREPORT de la utilidad Microsoft DUMPBIN.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257681"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> La opción/ERRORREPORT está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Sintaxis

> **/Errorreport**\[**NONE** \| **prompt** \| **Queue** \| **send** ]

## <a name="remarks"></a>Observaciones

La configuración del servicio Informe de errores de Windows invalida los argumentos **/errorreport** . DUMPBIN envía automáticamente informes de errores internos a Microsoft, si los informes se habilitan mediante Informe de errores de Windows. No se envía ningún informe si está deshabilitado por Informe de errores de Windows.

## <a name="see-also"></a>Consulte también

[Opciones de DUMPBIN](dumpbin-options.md)
