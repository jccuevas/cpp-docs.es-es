---
title: . ILK (archivos) como entrada del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3b8de3758daf59a543cdcc9f3b73e1d6c6f0ce8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720595"
---
# <a name="ilk-files-as-linker-input"></a>Archivos .Ilk como entrada del vinculador

Cuando se vinculan de forma incremental, LINK actualiza el archivo de estado .ilk que creó durante la primera vinculación incremental. Este archivo tiene el mismo nombre base que el archivo .exe o .dll, y tiene la extensión .ilk. VÍNCULO durante posteriores vínculos incrementales, actualiza el archivo .ilk. Si falta el archivo .ilk, LINK realizará un vínculo completo y crea un archivo .ilk nuevo. Si el archivo .ilk está inutilizable, LINK realizará un vínculo no incremental. Para obtener más información sobre la vinculación incremental, vea la [vincular de forma incremental (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opción.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)