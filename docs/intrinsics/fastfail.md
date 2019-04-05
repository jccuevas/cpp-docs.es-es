---
title: __fastfail
ms.date: 11/04/2016
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: a9f75cbf3c572401ef26fb16ced221eb24d35534
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041514"
---
# <a name="fastfail"></a>__fastfail

**Específicos de Microsoft**

Finaliza inmediatamente el proceso de llamada con un mínimo de sobrecarga.

## <a name="syntax"></a>Sintaxis

```
void __fastfail(unsigned int code);
```

#### <a name="parameters"></a>Parámetros

*code*<br/>
[in] Un `FAST_FAIL_<description>` constante simbólica de winnt.h o wdm.h que indica el motivo de la terminación del proceso.

## <a name="return-value"></a>Valor devuelto

No se devuelve el intrínseco `__fastfail`.

## <a name="remarks"></a>Comentarios

El `__fastfail` intrínseco proporciona un mecanismo para un *rápida por error* solicitud, una manera de terminación inmediata del proceso de solicitud para un proceso posiblemente dañado. El recurso de control de excepciones normales no puede controlar los errores críticos que pueden haber dañado el estado del programa y que se acumulan sin posibilidad de recuperación. Use `__fastfail` para terminar el proceso con una sobrecarga mínima.

Internamente, `__fastfail` se implementa mediante el uso de varios mecanismos específicos de la arquitectura:

|Arquitectura|Instrucción|Ubicación del argumento de código|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|ecx|
|x64|int 0x29|rcx|
|ARM|Código de operación 0xDEFB|r0|
|ARM64|0xF003 OpCode|x0|

Una solicitud de error rápido es independiente y normalmente solo requiere dos instrucciones para ejecutarse. Una vez que se ha ejecutado una solicitud de error rápido, el kernel toma las medidas oportunas. En el código en modo de usuario no hay ninguna dependencia de memoria, aparte del puntero de la instrucción cuando se provoca un evento de error rápido. Esto maximiza la fiabilidad, incluso si hay daños graves en la memoria.

El argumento `code` (una de las constantes simbólicas `FAST_FAIL_<description>` de winnt.h or wdm.h) describe el tipo de condición de error y se incorpora en los informes de error de una manera específica del entorno.

Las solicitudes de error rápido en modo de usuario aparecen como una segunda excepción no continuable con el código de excepción 0xC0000409 y por lo menos con un parámetro de excepción. El primer parámetro de excepción es el valor `code`. Este código de excepción indica al Informe de errores de Windows (WER) y a la infraestructura de depuración que el proceso está dañado y que se deben realizar acciones mínimas en el proceso en respuesta al error. Las solicitudes de error rápido en modo kernel se implementan mediante un código dedicado de comprobación de errores, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). En ambos casos, no se invocan controladores de excepciones, ya que se espera que el programa esté en un estado dañado. Si hay presente un depurador, se le ofrece la oportunidad de examinar el estado del programa antes de la finalización.

La compatibilidad con el mecanismo de error rápido nativo comenzó en Windows 8. Los sistemas operativos de Windows que no son compatibles con la instrucción de error rápido de forma nativa normalmente tratarán una solicitud de error rápido como una infracción de acceso, o como una comprobación de errores `UNEXPECTED_KERNEL_MODE_TRAP`. En estos casos, el programa también se cierra, pero no necesariamente de una forma tan rápida.

`__fastfail` solo está disponible como intrínseco.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
