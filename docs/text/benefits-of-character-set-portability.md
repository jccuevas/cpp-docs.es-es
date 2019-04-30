---
title: Ventajas de la portabilidad de los juegos de caracteres
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 0ca7e46cabb2d98a64a244863f8574a3e9e2a456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410790"
---
# <a name="benefits-of-character-set-portability"></a>Ventajas de la portabilidad de los juegos de caracteres

Puede beneficiarse del uso de las características de portabilidad de tiempo de ejecución de C y MFC incluso aunque no piense actualmente internacionalizar su aplicación:

- Código portable hace que el código base flexible. Más adelante se puede mover fácilmente a Unicode o MBCS.

- El uso de Unicode hace que las aplicaciones para Windows más eficaz. Dado que Windows utiliza Unicode, se deben traducir cadenas no Unicode que se pasan a y desde el sistema operativo que incurre en sobrecarga.

## <a name="see-also"></a>Vea también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Compatibilidad con Unicode](../text/support-for-unicode.md)
