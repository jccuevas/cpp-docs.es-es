---
title: Funciones globales COM de compilador
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: c0a9c742ad9dcbb05ed2d78c954d5a597e3b57cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189785"
---
# <a name="compiler-com-global-functions"></a>Funciones globales COM de compilador

**Específicos de Microsoft**

Están disponibles las siguientes rutinas:

|Función|Descripción|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Produce una [_com_error](../cpp/com-error-class.md) en respuesta a un error.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Reemplaza la función predeterminada que se utiliza para el control de errores de COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convierte un valor `BSTR` en un objeto `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convierte un valor `char *` en un objeto `BSTR`.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)
