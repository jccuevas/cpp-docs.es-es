---
title: /ERRORREPORT (editbin.exe)
description: Referencia de la opción de línea de comandos/ERRORREPORT de la utilidad Microsoft EDITBIN.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_editbin
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 4456a49cc53b21bd24c616852159ca299181071b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439904"
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
