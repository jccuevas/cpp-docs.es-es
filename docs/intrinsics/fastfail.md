---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222188"
---
# <a name="__fastfail"></a>__fastfail

**Específicos de Microsoft**

Finaliza inmediatamente el proceso de llamada con un mínimo de sobrecarga.

## <a name="syntax"></a>Sintaxis

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>Parámetros

*codifica*\
de Una `FAST_FAIL_<description>` constante simbólica de Winnt. h o WDM. h que indica la razón de la finalización del proceso.

## <a name="return-value"></a>Valor devuelto

No se devuelve el intrínseco `__fastfail`.

## <a name="remarks"></a>Comentarios

El `__fastfail` intrínseco proporciona un mecanismo para una solicitud de *error rápido* , una manera de que un proceso potencialmente dañado solicite la terminación inmediata del proceso. El recurso de control de excepciones normales no puede controlar los errores críticos que pueden haber dañado el estado del programa y que se acumulan sin posibilidad de recuperación. Use `__fastfail` para terminar el proceso con una sobrecarga mínima.

Internamente, `__fastfail` se implementa mediante el uso de varios mecanismos específicos de la arquitectura:

|Arquitectura|Instrucción|Ubicación del argumento de código|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|x64|int 0x29|`rcx`|
|ARM|Código de operación 0xDEFB|`r0`|
|ARM64|Código de operación 0xF003|`x0`|

Una solicitud de error rápido es independiente y normalmente solo requiere dos instrucciones para ejecutarse. Después de ejecutar una solicitud de error rápido, el kernel toma la acción adecuada. En el código en modo de usuario no hay ninguna dependencia de memoria, aparte del puntero de la instrucción cuando se provoca un evento de error rápido. Esto maximiza su confiabilidad, incluso en caso de daños graves en la memoria.

El `code` argumento, una de las `FAST_FAIL_<description>` constantes simbólicas de Winnt. h o WDM. h, describe el tipo de condición de error. Se incorpora a los informes de errores de una manera específica del entorno.

Las solicitudes de error rápido en modo de usuario aparecen como una excepción de segunda oportunidad no continuada con el código de excepción 0xC0000409 y con al menos un parámetro de excepción. El primer parámetro de excepción es el valor `code`. Este código de excepción indica al Informe de errores de Windows (WER) y a la infraestructura de depuración que el proceso está dañado, y que las acciones en proceso mínimas deben realizarse en respuesta al error. Las solicitudes de error rápido en modo kernel se implementan mediante un código dedicado de comprobación de errores, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). En ambos casos, no se invocan controladores de excepciones, ya que se espera que el programa esté en un estado dañado. Si hay un depurador, se le da la oportunidad de examinar el estado del programa antes de la finalización.

La compatibilidad con el mecanismo de error rápido nativo comenzó en Windows 8. Los sistemas operativos Windows que no admiten la instrucción de error rápido de forma nativa normalmente tratarán una solicitud de error rápido como una infracción de acceso o como una `UNEXPECTED_KERNEL_MODE_TRAP` comprobación de errores. En estos casos, el programa también se cierra, pero no necesariamente de una forma tan rápida.

`__fastfail` solo está disponible como intrínseco.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
