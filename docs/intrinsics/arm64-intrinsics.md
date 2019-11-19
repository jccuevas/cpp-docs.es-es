---
title: Intrínsecos ARM64
description: Una lista de los intrínsecos de ARM64 admitidos por C++ el compilador de Microsoft.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 30881c2b45714f91bf9035819b11ae41322b7086
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163686"
---
# <a name="arm64-intrinsics"></a>Intrínsecos ARM64

El compilador de Microsoft C++ (MSVC) hace que los siguientes intrínsecos estén disponibles en la arquitectura ARM64. Para más información sobre ARM, consulte las secciones sobre arquitectura y herramientas de desarrollo de software en el sitio web de [documentación para desarrolladores de ARM](https://developer.arm.com/docs) .

## <a name="top"></a>NEON

Las extensiones del conjunto de instrucciones de vector de neón para ARM64 proporcionan funcionalidades de Single Instruction Multiple Data (SIMD). Son similares a las de los conjuntos de instrucciones de vector de MMX y SSE que son comunes a los procesadores de arquitectura x86 y x64.

Se admiten las funciones intrínsecas de neón, como se proporciona en el archivo de encabezado *arm64_neon. h*. La compatibilidad de MSVC con los intrínsecos de neón es similar a la del compilador de ARM64, que se documenta en la [referencia intrínseca de neón de ARM](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) en el sitio web de INFOCENTER para ARM.

##  <a name="A"></a>Lista de intrínsecos específicos de ARM64

|Nombre de la función|Instrucción|Prototipo de función|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (unsigned Long, unsigned char)|
|__addx18word||void __addx18word (unsigned Long, unsigned short)|
|__addx18dword||void __addx18dword (unsigned Long, unsigned Long)|
|__addx18qword||void __addx18qword (unsigned Long, unsigned __int64)|
|__cas8|CASB|unsigned __int8 __cas8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__cas16|Tesorería|unsigned __int16 __cas16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__cas32|CAS|unsigned __int32 __cas32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__cas64|CAS|unsigned __int64 __cas64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casa8|CASAB|unsigned __int8 __casa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casa16|CASAH|unsigned __int16 __casa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casa32|CASA|unsigned __int32 __casa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casa64|CASA|unsigned __int64 __casa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casl8|CASLB|unsigned __int8 __casl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casl16|CASLH|unsigned __int16 __casl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casl32|CASL|unsigned __int32 __casl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casl64|CASL|unsigned __int64 __casl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casal8|CASALB|unsigned __int8 __casal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casal16|CASALH|unsigned __int16 __casal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casal32|CASAL|unsigned __int32 __casal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casal64|CASAL|unsigned __int64 __casal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__crc32b|CRC32B|__int32 sin signo __crc32b (__int32 sin signo, __int32 sin signo)|
|__crc32h|CRC32H|__int32 sin signo __crc32h (__int32 sin signo, __int32 sin signo)|
|__crc32w|CRC32W|__int32 sin signo __crc32w (__int32 sin signo, __int32 sin signo)|
|__crc32d|CRC32X|__int32 sin signo __crc32d (__int32 sin signo, __int64 sin signo)|
|__crc32cb|CRC32CB|__int32 sin signo __crc32cb (__int32 sin signo, __int32 sin signo)|
|__crc32ch|CRC32CH|__int32 sin signo __crc32ch (__int32 sin signo, __int32 sin signo)|
|__crc32cw|CRC32CW|__int32 sin signo __crc32cw (__int32 sin signo, __int32 sin signo)|
|__crc32cd|CRC32CX|__int32 sin signo __crc32cd (__int32 sin signo, __int64 sin signo)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información sobre los tipos de restricciones que se pueden aplicar, consulte restricciones de la [barrera de memoria](#BarrierRestrictions).|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información sobre los tipos de restricciones que se pueden aplicar, consulte restricciones de la [barrera de memoria](#BarrierRestrictions).|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información sobre los tipos de restricciones que se pueden aplicar, consulte restricciones de la [barrera de memoria](#BarrierRestrictions).|
|__getReg||unsigned __int64 __getReg (int)|
|__getRegFp||Double __getRegFp (int)|
|__getCallerReg||unsigned __int64 __getCallerReg (int)|
|__getCallerRegFp||Double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt (unsigned int,...)|
|__incx18byte||void __incx18byte (unsigned Long)|
|__incx18word||void __incx18word (unsigned Long)|
|__incx18dword||void __incx18dword (unsigned Long)|
|__incx18qword||void __incx18qword (unsigned Long)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 \*)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 \*)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 \*)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (\_volátil _int16 \*, \__int16)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (\_volátil _int32 \*, \__int32)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (\_volátil _int64 \*, \__int64)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (\_volátil _int8 \*, \__int8)<br /><br /> Para obtener más información, vea [__iso_volatile_load intrínsecos de/Store](#IsoVolatileLoadStore).|
|__ldar8|LDARB|unsigned __int8 __ldar8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|unsigned __int16 __ldar16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|unsigned __int32 __ldar32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|unsigned __int64 __ldar64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|unsigned __int8 __ldapr8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|unsigned __int16 __ldapr16 (unsigned __int16 volatile * _Target)|
|__ldapr32|LDAPr|unsigned __int32 __ldapr32 (unsigned __int32 volatile * _Target)|
|__ldapr64|LDAPr|unsigned __int64 __ldapr64 (unsigned __int64 volatile * _Target)|
|__mulh||\__int64 __mulh (\__int64, \__int64)|
|__prefetch|PRFM|void __cdecl \__prefetch (const void \*)<br /><br /> Proporciona una sugerencia de memoria `PRFM` con la operación de captura previa `PLDL1KEEP` al sistema al que se puede acceder pronto a la dirección especificada o cerca de ella. Algunos sistemas pueden optar por optimizarse para que ese modelo de acceso a memoria aumente el rendimiento en tiempo de ejecución. Sin embargo, desde el punto de vista del lenguaje C++, la función no tiene ningún efecto observable y podría no hacer nada.|
|__prefetch2|PRFM|void __cdecl \__prefetch (const void \*, uint8_t prfop)<br /><br /> Proporciona una `PRFM` sugerencia de memoria con la operación de captura previa proporcionada al sistema en la que se puede tener acceso a la memoria o cerca de la dirección especificada en breve. Algunos sistemas pueden optar por optimizarse para que ese modelo de acceso a memoria aumente el rendimiento en tiempo de ejecución. Sin embargo, desde el punto de vista del lenguaje C++, la función no tiene ningún efecto observable y podría no hacer nada.|
|__readx18byte||unsigned char __readx18byte (unsigned Long)|
|__readx18word||unsigned short __readx18word (unsigned Long)|
|__readx18dword||unsigned Long __readx18dword (unsigned Long)|
|__readx18qword||__int64 sin signo __readx18qword (unsigned Long)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, Double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, Double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int, const char \*)|
|__stlr8|STLRB|void __stlr8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__stlr32|STLR|void __stlr32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__stlr64|STLR|void __stlr64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swp8|SWPB|unsigned __int8 __swp8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swp16|SWPH|unsigned __int16 __swp16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swp32|SWP|unsigned __int32 __swp32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swp64|SWP|unsigned __int64 __swp64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpa8|SWPAB|unsigned __int8 __swpa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpa16|SWPAH|unsigned __int16 __swpa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpa32|SWPA|unsigned __int32 __swpa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpa64|SWPA|unsigned __int64 __swpa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpl8|SWPLB|unsigned __int8 __swpl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpl16|SWPLH|unsigned __int16 __swpl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpl32|SWPL|unsigned __int32 __swpl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpl64|SWPL|unsigned __int64 __swpl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpal8|SWPALB|unsigned __int8 __swpal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpal16|SWPALH|unsigned __int16 __swpal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpal32|SWPAL|unsigned __int32 __swpal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpal64|SWPAL|unsigned __int64 __swpal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__sys|Sist|unsigned int __sys (int, __int64)|
|__svc|SVC|unsigned int __svc (unsigned int,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (unsigned Long, unsigned char)|
|__writex18word||void __writex18word (unsigned Long, unsigned short)|
|__writex18dword||void __writex18dword (unsigned Long, unsigned Long)|
|__writex18qword||void __writex18qword (unsigned Long, unsigned __int64)|
|__umulh||unsigned \__int64 __umulh (unsigned \__int64, unsigned \__int64)|
|_CopyDoubleFromInt64||doble _CopyDoubleFromInt64 (_int64\_)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 flotante (\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||_CountLeadingOnes64 int sin signo (_int64 \_sin signo)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64 (\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||_CountLeadingZeros64 int sin signo (_int64 \_sin signo)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \__int64)|

[[Volver al principio](#top)]

###  <a name="BarrierRestrictions"></a>Restricciones de la barrera de memoria

Las funciones intrínsecas `__dmb` (barrera de memoria de datos), `__dsb` (barrera de sincronización de datos) y `__isb` (barrera de sincronización de instrucciones) usan los siguientes valores predefinidos para especificar la restricción de barrera de memoria en términos del dominio de uso compartido y el tipo de acceso que se ve afectado por la operación.

|Valor de restricción|Descripción|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Todo el sistema, lectura y escritura.|
|_ARM64_BARRIER_ST|Todo el sistema, solo escritura.|
|_ARM64_BARRIER_LD|Sistema completo, solo lectura.|
|_ARM64_BARRIER_ISH|Puede compartirse internamente, lectura y escritura.|
|_ARM64_BARRIER_ISHST|Puede compartirse internamente, solo escritura.|
|_ARM64_BARRIER_ISHLD|Interno compartible, solo lectura.|
|_ARM64_BARRIER_NSH|No puede compartirse, lectura y escritura.|
|_ARM64_BARRIER_NSHST|No puede compartirse, solo escritura.|
|_ARM64_BARRIER_NSHLD|No compartible, de solo lectura.|
|_ARM64_BARRIER_OSH|Puede compartirse externamente, lectura y escritura.|
|_ARM64_BARRIER_OSHST|Puede compartirse externamente, solo escritura.|
|_ARM64_BARRIER_OSHLD|Compartido externo, solo lectura.|

Para el `__isb` intrínseco, la única restricción que es válida actualmente es _ARM64_BARRIER_SY; todos los demás valores están reservados por la arquitectura.

###  <a name="IsoVolatileLoadStore"></a>__iso_volatile_load intrínsecos/Store

Estas funciones intrínsecas realizan explícitamente cargas y almacenes que no están sujetos a las optimizaciones del compilador.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Parámetros

\ de *Ubicación*
La dirección de una ubicación de memoria para leer o escribir.

*Valor*\
Valor que se va a escribir en la ubicación de memoria especificada (solo intrínsecos de almacén).

#### <a name="return-value-load-intrinsics-only"></a>Valor devuelto (solo intrínsecos de carga)

El valor de la ubicación de memoria especificada por la *Ubicación*.

#### <a name="remarks"></a>Comentarios

Puede usar los intrínsecos `__iso_volatile_load8/16/32/64` y `__iso_volatile_store8/16/32/64` para realizar explícitamente accesos a memoria que no están sujetos a las optimizaciones del compilador. El compilador no puede quitar, sintetizar ni cambiar el orden relativo de estas operaciones. Sin embargo, no genera barreras de memoria de hardware implícitas. Por lo tanto, el hardware todavía puede reordenar los accesos de memoria observables en varios subprocesos. Más concretamente, estos intrínsecos son equivalentes a las siguientes expresiones compiladas en **/volatile: ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Observe que los intrínsecos tienen punteros volátiles para dar cabida a variables volátiles. Sin embargo, no hay ningún requisito o recomendación para usar punteros volátiles como argumentos. La semántica de estas operaciones es exactamente la misma si se usa un tipo no volátil normal.

Para obtener más información sobre el argumento de línea de comandos **/volatile: ISO** , consulte [/volatile (interpretación de la palabra clave volatile)](../build/reference/volatile-volatile-keyword-interpretation.md).

##  <a name="I"></a>Compatibilidad de ARM64 con intrínsecos de otras arquitecturas

En la tabla siguiente se enumeran los intrínsecos de otras arquitecturas que se admiten en plataformas ARM64. Cuando el comportamiento de un intrínseco en ARM64 difiere de su comportamiento en otras arquitecturas de hardware, se indican detalles adicionales.

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|void __cdecl \__debugbreak (void)|
|__fastfail|__declspec (noreturn) void \__fastfail (unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield (void) **Note:** en plataformas ARM64, esta función genera la instrucción yield. Esta instrucción indica que el subproceso está realizando una tarea que se puede suspender temporalmente de la ejecución (por ejemplo, un Spinlock) sin afectar negativamente al programa. Permite a la CPU ejecutar otras tareas durante los ciclos de ejecución que de otro modo se desperdiciarían.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|unsigned char _BitScanForward (unsigned Long \* _Index, unsigned Long _Mask)|
|_BitScanForward64|unsigned char _BitScanForward64 (unsigned Long \* _Index, unsigned __int64 _Mask)|
|_BitScanReverse|unsigned char _BitScanReverse (unsigned Long \* _Index, unsigned Long _Mask)|
|_BitScanReverse64|unsigned char _BitScanReverse64 (unsigned Long \* _Index, unsigned __int64 _Mask)|
|_bittest|unsigned char _bittest (Long const \*, Long)|
|_bittest64|unsigned char _bittest64 (__int64 const \*, __int64)|
|_bittestandcomplement|unsigned char _bittestandcomplement (Long \*, Long)|
|_bittestandcomplement64|unsigned char _bittestandcomplement64 (__int64 \*, __int64)|
|_bittestandreset|unsigned char _bittestandreset (Long \*, Long)|
|_bittestandreset64|unsigned char _bittestandreset64 (__int64 \*, __int64)|
|_bittestandset|unsigned char _bittestandset (Long \*, Long)|
|_bittestandset64|unsigned char _bittestandset64 (__int64 \*, __int64)|
|_byteswap_uint64|unsigned __int64 \__cdecl _byteswap_uint64 (\_sin signo _int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void) **Nota:** en las plataformas ARM64, esta función genera la instrucción `MSR DAIFCLR,#2`; solo está disponible como intrínseco.|
|_enable|void __cdecl _enable (void) **Nota:** en las plataformas ARM64, esta función genera la instrucción `MSR DAIFSET,#2`; solo está disponible como intrínseco.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|unsigned __int64 \__cdecl _rotl64 (unsigned \__int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|unsigned __int64 \__cdecl _rotr64 (unsigned \__int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Volver al principio](#top)]

## <a name="interlocked-intrinsics"></a>Intrínsecos entrelazados

Los intrínsecos entrelazados son un conjunto de intrínsecos que se usan para realizar operaciones atómicas de lectura-modificación-escritura. Algunos de ellos son comunes a todas las plataformas. Aquí se enumeran por separado porque hay un gran número de ellos. Dado que sus definiciones son principalmente redundantes, es más fácil pensar en ellas en términos generales. Sus nombres pueden utilizarse para derivar los comportamientos exactos.

En la tabla siguiente se resume la compatibilidad de ARM64 de los intrínsecos entrelazados que no son de la misma. Cada celda de la tabla corresponde a un nombre que se crea agregando el nombre de la operación de la celda del extremo izquierdo de la fila y el nombre de tipo de la celda de la parte superior de la columna a `_Interlocked`. Por ejemplo, la celda en la intersección de la fila de `Xor` y la columna de `8` corresponde a `_InterlockedXor8` y es totalmente compatible. La mayoría de las funciones admitidas ofrecen estos sufijos opcionales: `_acq`, `_rel` y `_nf`. El sufijo `_acq` indica una semántica de "adquisición" y el sufijo `_rel` indica una semántica de "versión". El sufijo `_nf` o "no barrera" es único para ARM y ARM64 y se describe en la sección siguiente.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Agregar|Ninguno|Ninguno|Completo|Completo|Ninguno|Ninguno|
|y|Completo|Completo|Completo|Completo|Ninguno|Ninguno|
|CompareExchange|Completo|Completo|Completo|Completo|Completo|Completo|
|Decremento|Ninguno|Completo|Completo|Completo|Ninguno|Ninguno|
|Exchange|Completo|Completo|Completo|Completo|Ninguno|Completo|
|ExchangeAdd|Completo|Completo|Completo|Completo|Ninguno|Ninguno|
|Incremento|Ninguno|Completo|Completo|Completo|Ninguno|Ninguno|
|O bien|Completo|Completo|Completo|Completo|Ninguno|Ninguno|
|Xor|Completo|Completo|Completo|Completo|Ninguno|Ninguno|

Explicación:

- **Full**: admite formularios sin formato, `_acq`, `_rel`y `_nf`.

- **Ninguno**: no compatible

###  <a name="nf_suffix"></a>sufijo _nf (sin barrera)

El sufijo `_nf` o "no barrera" indica que la operación no se comporta como ningún tipo de barrera de memoria, a diferencia de las otras tres formas (sin formato, `_acq`y `_rel`), que se comportan como algún tipo de barrera. Un uso posible de los formularios de `_nf` es mantener un contador estadístico actualizado por varios subprocesos al mismo tiempo, pero cuyo valor no se utiliza de otra manera mientras se ejecutan varios subprocesos.

### <a name="list-of-interlocked-intrinsics"></a>Lista de intrínsecos entrelazados

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|_InterlockedAdd|Long _InterlockedAdd (Long _volatile \*, Long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAdd_acq|Long _InterlockedAdd_acq (Long volatile \*, Long)|
|_InterlockedAdd_nf|Long _InterlockedAdd_nf (Long volatile \*, Long)|
|_InterlockedAdd_rel|Long _InterlockedAdd_rel (Long volatile \*, Long)|
|_InterlockedAnd|Long _InterlockedAnd (Long volatile \*, Long)|
|_InterlockedAnd16|Short _InterlockedAnd16 (Short volatile \*, Short)|
|_InterlockedAnd16_acq|Short _InterlockedAnd16_acq (Short volatile \*, Short)|
|_InterlockedAnd16_nf|Short _InterlockedAnd16_nf (Short volatile \*, Short)|
|_InterlockedAnd16_rel|Short _InterlockedAnd16_rel (Short volatile \*, Short)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (char volatile \*, Char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (char volatile \*, Char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char volatile \*, Char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (char volatile \*, Char)|
|_InterlockedAnd_acq|Long _InterlockedAnd_acq (Long volatile \*, Long)|
|_InterlockedAnd_nf|Long _InterlockedAnd_nf (Long volatile \*, Long)|
|_InterlockedAnd_rel|Long _InterlockedAnd_rel (Long volatile \*, Long)|
|_InterlockedCompareExchange|Long __cdecl _InterlockedCompareExchange (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange_acq|Long _InterlockedCompareExchange_acq (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange_nf|Long _InterlockedCompareExchange_nf (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange_rel|Long _InterlockedCompareExchange_rel (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange16|Short _InterlockedCompareExchange16 (Short volatile \*, Short, Short)|
|_InterlockedCompareExchange16_acq|Short _InterlockedCompareExchange16_acq (Short volatile \*, Short, Short)|
|_InterlockedCompareExchange16_nf|Short _InterlockedCompareExchange16_nf (Short volatile \*, Short, Short)|
|_InterlockedCompareExchange16_rel|Short _InterlockedCompareExchange16_rel (Short volatile \*, Short, Short)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile \*, Char, Char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchange128|unsigned char _InterlockedCompareExchange128 (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|unsigned char _InterlockedCompareExchange128_acq (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|unsigned char _InterlockedCompareExchange128_nf (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char _InterlockedCompareExchange128_rel (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedDecrement|Long __cdecl _InterlockedDecrement (Long volatile \*)|
|_InterlockedDecrement16|Short _InterlockedDecrement16 (Short volatile \*)|
|_InterlockedDecrement16_acq|Short _InterlockedDecrement16_acq (Short volatile \*)|
|_InterlockedDecrement16_nf|Short _InterlockedDecrement16_nf (Short volatile \*)|
|_InterlockedDecrement16_rel|Short _InterlockedDecrement16_rel (Short volatile \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\__int64 volatile \*)|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatile \*)|
|_InterlockedDecrement_acq|Long _InterlockedDecrement_acq (Long volatile \*)|
|_InterlockedDecrement_nf|Long _InterlockedDecrement_nf (Long volatile \*)|
|_InterlockedDecrement_rel|Long _InterlockedDecrement_rel (Long volatile \*)|
|_InterlockedExchange|Long __cdecl _InterlockedExchange (Long volatile \* _Target, Long)|
|_InterlockedExchange_acq|Long _InterlockedExchange_acq (Long volatile \* _Target, Long)|
|_InterlockedExchange_nf|Long _InterlockedExchange_nf (Long volatile \* _Target, Long)|
|_InterlockedExchange_rel|Long _InterlockedExchange_rel (Long volatile \* _Target, Long)|
|_InterlockedExchange16|Short _InterlockedExchange16 (Short volatile \* _Target, Short)|
|_InterlockedExchange16_acq|Short _InterlockedExchange16_acq (Short volatile \* _Target, Short)|
|_InterlockedExchange16_nf|Short _InterlockedExchange16_nf (Short volatile \* _Target, Short)|
|_InterlockedExchange16_rel|Short _InterlockedExchange16_rel (Short volatile \* _Target, Short)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char volatile \* _Target, Char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char volatile \* _Target, Char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target, Char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char volatile \* _Target, Char)|
|_InterlockedExchangeAdd|Long __cdecl _InterlockedExchangeAdd (Long volatile \*, Long)|
|_InterlockedExchangeAdd16|Short _InterlockedExchangeAdd16 (Short volatile \*, Short)|
|_InterlockedExchangeAdd16_acq|Short _InterlockedExchangeAdd16_acq (Short volatile \*, Short)|
|_InterlockedExchangeAdd16_nf|Short _InterlockedExchangeAdd16_nf (Short volatile \*, Short)|
|_InterlockedExchangeAdd16_rel|Short _InterlockedExchangeAdd16_rel (Short volatile \*, Short)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (char volatile \*, Char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (char volatile \*, Char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (char volatile \*, Char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (char volatile \*, Char)|
|_InterlockedExchangeAdd_acq|Long _InterlockedExchangeAdd_acq (Long volatile \*, Long)|
|_InterlockedExchangeAdd_nf|Long _InterlockedExchangeAdd_nf (Long volatile \*, Long)|
|_InterlockedExchangeAdd_rel|Long _InterlockedExchangeAdd_rel (Long volatile \*, Long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target, void \*)|
|_InterlockedIncrement|Long __cdecl _InterlockedIncrement (Long volatile \*)|
|_InterlockedIncrement16|Short _InterlockedIncrement16 (Short volatile \*)|
|_InterlockedIncrement16_acq|Short _InterlockedIncrement16_acq (Short volatile \*)|
|_InterlockedIncrement16_nf|Short _InterlockedIncrement16_nf (Short volatile \*)|
|_InterlockedIncrement16_rel|Short _InterlockedIncrement16_rel (Short volatile \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 volatile \*)|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\__int64 volatile \*)|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\__int64 volatile \*)|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 volatile \*)|
|_InterlockedIncrement_acq|Long _InterlockedIncrement_acq (Long volatile \*)|
|_InterlockedIncrement_nf|Long _InterlockedIncrement_nf (Long volatile \*)|
|_InterlockedIncrement_rel|Long _InterlockedIncrement_rel (Long volatile \*)|
|_InterlockedOr|Long _InterlockedOr (Long volatile \*, Long)|
|_InterlockedOr16|Short _InterlockedOr16 (Short volatile \*, Short)|
|_InterlockedOr16_acq|Short _InterlockedOr16_acq (Short volatile \*, Short)|
|_InterlockedOr16_nf|Short _InterlockedOr16_nf (Short volatile \*, Short)|
|_InterlockedOr16_rel|Short _InterlockedOr16_rel (Short volatile \*, Short)|
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedOr8|char _InterlockedOr8 (char volatile \*, Char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char volatile \*, Char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char volatile \*, Char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (char volatile \*, Char)|
|_InterlockedOr_acq|Long _InterlockedOr_acq (Long volatile \*, Long)|
|_InterlockedOr_nf|Long _InterlockedOr_nf (Long volatile \*, Long)|
|_InterlockedOr_rel|Long _InterlockedOr_rel (Long volatile \*, Long)|
|_InterlockedXor|Long _InterlockedXor (Long volatile \*, Long)|
|_InterlockedXor16|Short _InterlockedXor16 (Short volatile \*, Short)|
|_InterlockedXor16_acq|Short _InterlockedXor16_acq (Short volatile \*, Short)|
|_InterlockedXor16_nf|Short _InterlockedXor16_nf (Short volatile \*, Short)|
|_InterlockedXor16_rel|Short _InterlockedXor16_rel (Short volatile \*, Short)|
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedXor8|char _InterlockedXor8 (char volatile \*, Char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (char volatile \*, Char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (char volatile \*, Char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (char volatile \*, Char)|
|_InterlockedXor_acq|Long _InterlockedXor_acq (Long volatile \*, Long)|
|_InterlockedXor_nf|Long _InterlockedXor_nf (Long volatile \*, Long)|
|_InterlockedXor_rel|Long _InterlockedXor_rel (Long volatile \*, Long)|

[[Volver al principio](#top)]

### <a name="_interlockedbittest-intrinsics"></a>intrínsecos de _interlockedbittest

Los intrínsecos de prueba de bits entrelazados son comunes a todas las plataformas. ARM64 agrega `_acq`, `_rel`y `_nf` variantes, que solo modifican la semántica de barrera de una operación, tal y como se describe en el [sufijo _nf (no barrera)](#nf_suffix) anteriormente en este artículo.

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset (Long volatile \*, Long)|
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq (Long volatile \*, Long)|
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf (Long volatile \*, Long)|
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel (Long volatile \*, Long)|
|_interlockedbittestandreset64|unsigned char _interlockedbittestandreset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_acq|unsigned char _interlockedbittestandreset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_nf|unsigned char _interlockedbittestandreset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_rel|unsigned char _interlockedbittestandreset64_rel (__int64 volatile \*, __int64)|
|_interlockedbittestandset|unsigned char _interlockedbittestandset (Long volatile \*, Long)|
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq (Long volatile \*, Long)|
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf (Long volatile \*, Long)|
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel (Long volatile \*, Long)|
|_interlockedbittestandset64|unsigned char _interlockedbittestandset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_acq|unsigned char _interlockedbittestandset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_nf|unsigned char _interlockedbittestandset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_rel|unsigned char _interlockedbittestandset64_rel (__int64 volatile \*, __int64)|

[[Volver al principio](#top)]

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[Intrínsecos de ARM](arm-intrinsics.md)\
\ de [Referencia del ensamblador de ARM](../assembler/arm/arm-assembler-reference.md)
[C++Referencia del lenguaje](../cpp/cpp-language-reference.md)
