---
title: Archivos .Ilk como entrada del vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 252c1cd6e17346954fce7ebf16134246da76ba57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293854"
---
# <a name="ilk-files-as-linker-input"></a>Archivos .Ilk como entrada del vinculador

Cuando se vinculan de forma incremental, LINK actualiza el archivo de estado .ilk que creó durante la primera vinculación incremental. Este archivo tiene el mismo nombre base que el archivo .exe o .dll, y tiene la extensión .ilk. VÍNCULO durante posteriores vínculos incrementales, actualiza el archivo .ilk. Si falta el archivo .ilk, LINK realizará un vínculo completo y crea un archivo .ilk nuevo. Si el archivo .ilk está inutilizable, LINK realizará un vínculo no incremental. Para obtener más información sobre la vinculación incremental, vea la [vincular de forma incremental (/ INCREMENTAL)](incremental-link-incrementally.md) opción.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](link-input-files.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
