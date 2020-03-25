---
title: Convenciones de llamada, parámetros y tipo de valor devuelto
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 90767141337512b053bb06a40823c4a22a8a4823
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169752"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Convenciones de llamada, parámetros y tipo de valor devuelto

El prototipo de la rutina del asistente es:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parámetros

*pidd*<br/>
`const` puntero a una `ImgDelayDescr` que contiene los desplazamientos de varios datos relacionados con la importación, una marca de tiempo para la información de enlace y un conjunto de atributos que proporcionan más información sobre el contenido del descriptor. Actualmente solo hay un atributo, `dlattrRva`, que indica que las direcciones del descriptor son direcciones virtuales relativas. Para obtener más información, consulte las declaraciones en *Delayimp. h*.

Para obtener la definición de la estructura de `PCImgDelayDescr`, vea [definiciones de estructura y constante](structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Un puntero a la ranura de la tabla de direcciones de importación de carga retrasada (IAT) que se actualiza con la dirección de la función importada. La rutina auxiliar necesita almacenar el mismo valor que devuelve en esta ubicación.

## <a name="expected-return-values"></a>Valores devueltos esperados

Si la función se ejecuta correctamente, devolverá la dirección de la función importada.

Si la función no se ejecuta correctamente, generará una excepción y devolverá 0. Se pueden generar tres tipos de excepciones:

- Parámetro no válido, que se produce si los atributos de `pidd` no se especifican correctamente.

- Error de `LoadLibrary` en la DLL especificada.

- Error de `GetProcAddress`.

Es su responsabilidad controlar estas excepciones.

## <a name="remarks"></a>Observaciones

La convención de llamada de la función del asistente es `__stdcall`. El tipo del valor devuelto no es relevante, por lo que se usa FARPROC. Esta función tiene vinculación de C.

El valor devuelto del asistente de carga retrasada tiene que almacenarse en la ubicación del puntero de función transferida, salvo que quiera que la rutina del asistente se use como enlace de notificación. En ese caso, su código será el responsable de buscar el puntero de función adecuado que deba devolver. Entonces, el código thunk generado por el enlazador tomará ese valor devuelto como el destino real de la importación y saltará a él directamente.

## <a name="sample"></a>Muestra

El siguiente código muestra cómo implementar una función de enlace simple.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Consulte también

[Descripción de la función auxiliar](understanding-the-helper-function.md)
