---
title: Funciones globales COM de compilador
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: ac74270cd020aa66ccc14ff314a00b388a038086
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399192"
---
# <a name="compiler-com-global-functions"></a>Funciones globales COM de compilador

**Específicos de Microsoft**

Están disponibles las siguientes rutinas:

|Función|Descripción|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Se produce un [_com_error](../cpp/com-error-class.md) en respuesta a un error.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Reemplaza la función predeterminada que se utiliza para el control de errores de COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convierte un `BSTR` valor a un `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convierte un `char *` valor a un `BSTR`.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)