---
title: set_unexpected (CRT)
ms.date: 11/04/2016
api_name:
- set_unexpected
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 77c8f0ae8c64423a656a2ebbe1fe3ef6dbe1b794
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948300"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

Instala su propia función de finalización a la que debe llamar **unexpected**.

## <a name="syntax"></a>Sintaxis

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parámetros

*unexpFunction*<br/>
Puntero a una función que se escribe para reemplazar la función **inesperada** .

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función de finalización anterior registrada por **_set_unexpected** para que la función anterior se pueda restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; Este valor puede ser **null**.

## <a name="remarks"></a>Comentarios

La función **set_unexpected** instala *unexpFunction* como la función a la que se llama **inesperada**. no se usa **inesperado** en C++ la implementación de control de excepciones actual. El tipo **unexpected_function** se define en EH. H como puntero a una función inesperada definida por el usuario, *unexpFunction* que devuelve **void**. La función *unexpFunction* personalizada no debe volver a su llamador.

```cpp
typedef void ( *unexpected_function )( );
```

De forma predeterminada, las llamadas **inesperadas** **finalizan**. Puede cambiar este comportamiento predeterminado si escribe su propia función de finalización y llama a **set_unexpected** con el nombre de la función como su argumento. **inesperadas** llama a la última función especificada como argumento para **set_unexpected**.

A diferencia de la función de terminación personalizada instalada por una llamada a **set_terminate**, se puede iniciar una excepción desde *unexpFunction*.

En un entorno multiproceso, las funciones inesperadas se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función inesperada. Por lo tanto, cada subproceso se encarga de su propio control inesperado.

En la implementación actual de Microsoft C++ del control de excepciones, las llamadas **inesperadas** **finalizan** de forma predeterminada y nunca se llama a la biblioteca en tiempo de ejecución de control de excepciones. No hay ninguna ventaja concreta para llamar a **inesperados** en lugar de **Finalizar**.

Hay un único controlador de **set_unexpected** para todos los archivos dll o exe vinculados dinámicamente. Aunque llame a **set_unexpected** , es posible que el controlador se reemplace por otro o que esté reemplazando un controlador establecido por otro archivo dll o exe.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
