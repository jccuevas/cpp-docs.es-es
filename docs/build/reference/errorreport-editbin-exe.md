---
title: /ERRORREPORT (editbin.exe)
description: Referencia de la opción de línea de comandos/ERRORREPORT de la utilidad Microsoft EDITBIN.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 6c2ec8b6cda7b794114ed38cfb72b885bf2e38a1
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257603"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> La opción/ERRORREPORT está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Sintaxis

> **/Errorreport** \[ **NONE** \| **prompt** \| **Queue** \| **send** ]

## <a name="remarks"></a>Observaciones

La configuración del servicio Informe de errores de Windows invalida los argumentos **/errorreport** . EDITBIN envía automáticamente informes de errores internos a Microsoft, si los informes se habilitan mediante Informe de errores de Windows. No se envía ningún informe si está deshabilitado por Informe de errores de Windows.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)
