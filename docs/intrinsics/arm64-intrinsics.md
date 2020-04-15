---
title: Intrínsecos de ARM64
description: Una lista de los elementos intrínsecos ARM64 admitidos por el compilador de Microsoft C++.
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
ms.openlocfilehash: 196518439445824ddf5a7a841b30eb816251ba60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368216"
---
# <a name="arm64-intrinsics"></a>Intrínsecos de ARM64

El compilador de Microsoft C++ (MSVC) hace que los siguientes elementos intrínsecos estén disponibles en la arquitectura ARM64. Para obtener más información acerca de ARM, consulte las secciones Herramientas de arquitectura y desarrollo de software del sitio web [documentación para desarrolladores](https://developer.arm.com/docs) de ARM.

## <a name="neon"></a><a name="top"></a>Neón

Las extensiones del conjunto de instrucciones vectoriales NEON para ARM64 proporcionan capacidades de datos múltiples de instrucción única (SIMD). Se asemejan a los de los conjuntos de instrucciones vectoriales MMX y SSE que son comunes a los procesadores de arquitectura x86 y x64.

Se admiten los elementos intrínsecos de NEON, tal como se proporciona en el archivo de encabezado *arm64_neon.h*. La compatibilidad de MSVC para los elementos intrínsecos de NEON es similar a la del compilador ARM64, que se documenta en la referencia intrínseca de [ARM NEON](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) en el sitio web de ARM Infocenter.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>Lista de intrínsecos específicos de ARM64

|Nombre de la función|Instrucción|Prototipo de función|
|-------------------|-----------------|------------------------|
|__break|Brk|vacío __break (int)|
|__addx18byte||vacío __addx18byte (sin signo long, unsigned char)|
|__addx18word||vacío __addx18word (sin signo largo, sin signo corto)|
|__addx18dword||vacío __addx18dword (sin firmar largo, sin signo largo)|
|__addx18qword||vacío __addx18qword (sin firmar largo, sin signo __int64)|
|__cas8|CASB|__cas8 __int8 sin signo (_Target sin signo__int8, _Comp __int8 sin signo, _Value __int8 sin signo)|
|__cas16|Efectivo|__cas16 __int16 sin signo (_Target sin signo __int16 volatile*, _Comp __int16 sin signo, _Value __int16 sin signo)|
|__cas32|CAS|__cas32 __int32 sin signo (_Target sin signo __int32, _Comp de __int32 sin signo, _Value __int32 sin signo)|
|__cas64|CAS|__cas64 de __int64 sin signo (_Target _Value _Value _Value _Value _Value _Value _Value _Value _Value _Value de _Value _Value _Value _Value sin signo __int64 _Value, _Comp sin __int64 signo, __int64 sin signo)|
|__casa8|CASAB|__casa8 __int8 sin signo (_Target sin signo__int8, _Comp __int8 sin signo, __int8 sin signo _Value)|
|__casa16|CASAH|__casa16 de __int16 sin signo (_Target sin signo __int16, _Comp __int16 sin signo, __int16 sin signo _Value)|
|__casa32|CASA|__casa32 __int32 sin signo (_Target __int32 volatile* sin signo, __int32 sin signo _Comp, _Value __int32 sin signo)|
|__casa64|CASA|__casa64 __int64 sin signo (_Target __int64 sin signo__int64, _Comp __int64 sin signo, _Value de __int64 sin signo)|
|__casl8|CASLB|__casl8 de __int8 sin signo (_Target sin signo __int8 volatile*, _Comp __int8 sin signo, _Value __int8 sin signo)|
|__casl16|CASLH|__casl16 __int16 sin signo (_Target __int16 sin signo volatile*, _Comp __int16 sin signo, _Value __int16 sin signo)|
|__casl32|Casl|__casl32 __int32 sin signo (_Target sin __int32 signo*, _Comp __int32 sin signo, _Value __int32 sin signo)|
|__casl64|Casl|__casl64 de __int64 sin signo (_Target sin __int64 signo, _Comp __int64 sin signo, _Value __int64 sin signo)|
|__casal8|CASALB|__casal8 __int8 sin signo (_Target __int8 volatile* sin signo, _Comp __int8 sin signo, __int8 sin signo _Value)|
|__casal16|CASALH|__casal16 __int16 sin signo (_Target sin signo__int16, _Comp __int16 sin signo, _Value __int16 sin signo)|
|__casal32|Casal|__casal32 de __int32 sin signo (_Target sin signo __int32, _Comp de __int32 sin signo, _Value __int32 sin signo)|
|__casal64|Casal|__casal64 de __int64 sin signo (_Target __int64 sin signo volatile*, _Comp __int64 sin signo, _Value __int64 sin signo)|
|__crc32b|CRC32B|__crc32b de __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32h|CRC32H|__crc32h __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32w|CRC32W|__crc32w __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32d|CRC32X|__crc32d __int32 sin signo (__int32 sin signo, __int64 sin signo)|
|__crc32cb|CRC32CB|__crc32cb de __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32ch|CRC32CH|__crc32ch __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32cw|CRC32CW|__crc32cw __int32 sin signo (__int32 sin signo, __int32 sin signo)|
|__crc32cd|CRC32CX|__crc32cd de __int32 sin signo (__int32 sin signo, __int64 sin signo)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información acerca de los tipos de restricciones que se pueden aplicar, consulte [Restricciones](#BarrierRestrictions)de barrera de memoria .|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información acerca de los tipos de restricciones que se pueden aplicar, consulte [Restricciones](#BarrierRestrictions)de barrera de memoria .|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Inserta una operación de barrera de memoria en la secuencia de instrucciones. El parámetro `_Type` especifica el tipo de restricción que impone la barrera.<br /><br /> Para obtener más información acerca de los tipos de restricciones que se pueden aplicar, consulte [Restricciones](#BarrierRestrictions)de barrera de memoria .|
|__getReg||__getReg de __int64 sin firmar (int)|
|__getRegFp||doble __getRegFp (int)|
|__getCallerReg||__getCallerReg __int64 sin signo (int)|
|__getCallerRegFp||doble __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|Hlt|int __hlt(unsigned int, ...)|
|__incx18byte||vacío __incx18byte (largo sin signo)|
|__incx18word||vacío __incx18word (largo sin signo)|
|__incx18dword||vacío __incx18dword (largo sin signo)|
|__incx18qword||vacío __incx18qword (largo sin signo)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16(const \_ \*volatile _int16 )<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32(const \_ \*volatile _int32 )<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64(const \_ \*volatile _int64 )<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8(const \_ \*_int8 volátil )<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store16||__iso_volatile_store16 del \_vacío \* \_(_int16 volátil, _int16)<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store32||vacío __iso_volatile_store32 \_ \*(_int32 \_volátil, _int32)<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store64||__iso_volatile_store64 del \_vacío \* \_(_int64 volátil, _int64)<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store8||__iso_volatile_store8 del \_vacío \* \_(_int8 volátil, _int8)<br /><br /> Para obtener más información, consulte [__iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__ldar8|LDARB|__ldar8 __int8 sin signo (_Target __int8 volátil* sin signo)|
|__ldar16|LDARH|__ldar16 __int16 sin signo (_Target __int16 sin signo*)|
|__ldar32|LDAR|__ldar32 __int32 sin signo (_Target __int32 sin signo*)|
|__ldar64|LDAR|__ldar64 de __int64 sin signo (_Target __int64 no firmados)|
|__ldapr8|LDAPRB|__ldapr8 __int8 sin signo (_Target __ldapr8 __int8 sin signo*)|
|__ldapr16|LDAPRH|__ldapr16 __int16 sin signo (_Target __int16 sin signo)|
|__ldapr32|LDAPR|__ldapr32 __int32 sin signo (_Target __int32 sin signo*)|
|__ldapr64|LDAPR|__ldapr64 de __int64 sin signo (_Target __int64 volátil* sin signo)|
|__mulh||\__int64 __mulh(_int64,\_ \__int64)|
|__prefetch|PRFM|vacío \___cdecl _prefetch(const void \*)<br /><br /> Proporciona `PRFM` una sugerencia de memoria `PLDL1KEEP` con la operación de captura previa al sistema a la que se puede acceder pronto a la memoria en o cerca de la dirección especificada. Algunos sistemas pueden optar por optimizarse para que ese modelo de acceso a memoria aumente el rendimiento en tiempo de ejecución. Sin embargo, desde el punto de vista del lenguaje C++, la función no tiene ningún efecto observable y podría no hacer nada.|
|__prefetch2|PRFM|vacío \___cdecl _prefetch (const void \*, uint8_t prfop)<br /><br /> Proporciona `PRFM` una sugerencia de memoria con la operación de captura previa proporcionada al sistema a la que se puede acceder pronto a la memoria en o cerca de la dirección especificada. Algunos sistemas pueden optar por optimizarse para que ese modelo de acceso a memoria aumente el rendimiento en tiempo de ejecución. Sin embargo, desde el punto de vista del lenguaje C++, la función no tiene ningún efecto observable y podría no hacer nada.|
|__readx18byte||char __readx18byte sin signo (sin signo)|
|__readx18word||unsigned short __readx18word (sin signo largo)|
|__readx18dword||unsigned long __readx18dword (sin signo largo)|
|__readx18qword||__readx18qword __int64 sin signo (largo sin signo)|
|__setReg||vacío __setReg (int, __int64 sin signo)|
|__setRegFp||vacío __setRegFp(int, double)|
|__setCallerReg||__setCallerReg nulo (int, __int64 sin firmar)|
|__setCallerRegFp||vacío __setCallerRegFp (int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||vacío __static_assert(int, const char \*)|
|__stlr8|STLRB|vacío __stlr8 (_Target sin signo __int8, _Value __int8 sin signo)|
|__stlr16|STLRH|__stlr16 void (_Target sin signo __int16, _Value de __int16 sin signo)|
|__stlr32|STLR|vacío __stlr32 (_Target sin __int32 signo*, _Value __int32 sin signo)|
|__stlr64|STLR|void __stlr64(sin signo __int64 volatile _Target*, _Value __int64 sin signo)|
|__swp8|SWPB|__swp8 de __int8 sin signo (_Target __int8 sin signo, _Value de __int8 sin signo)|
|__swp16|SWPH|__swp16 de __int16 sin signo (_Target __int16 sin signo, __int16 sin signo _Value)|
|__swp32|Swp|__swp32 __int32 sin signo (_Target __int32 sin signo, _Value __int32 sin signo)|
|__swp64|Swp|__swp64 __int64 sin signo (_Target sin signo __int64, _Value __int64 sin signo)|
|__swpa8|SWPAB|__swpa8 __int8 sin signo (_Target sin signo__int8, _Value __int8 sin signo)|
|__swpa16|SWPAH|__swpa16 __int16 sin signo (_Target __int16 volátiles sin signo, _Value __int16 sin signo)|
|__swpa32|SWPA|__swpa32 __int32 sin signo (_Target __int32 sin signo, _Value __int32 sin signo)|
|__swpa64|SWPA|__swpa64 __int64 sin signo (_Target sin signo__int64, _Value de __int64 sin signo)|
|__swpl8|SWPLB|__swpl8 __int8 sin signo (_Target __int8 sin signo, _Value __int8 sin signo)|
|__swpl16|SWPLH|__swpl16 de __int16 sin signo (_Target __swpl16 __swpl16 sin signo __int16, _Value __int16 sin signo)|
|__swpl32|SWPL|__swpl32 de __int32 sin signo (_Target __int32 sin signo, _Target __int32 sin signo _Value)|
|__swpl64|SWPL|__swpl64 __int64 sin signo (_Target __int64 sin signo, __int64 __int64 _Value)|
|__swpal8|SWPALB|__swpal8 de __int8 sin signo (_Target __int8 sin signo, _Value de __int8 sin signo)|
|__swpal16|SWPALH|__swpal16 __int16 sin signo (_Target __int16 sin signo, _Value __int16 sin signo)|
|__swpal32|SWPAL|__swpal32 de __int32 sin signo (_Target __int32 sin signo, _Value __int32 sin signo)|
|__swpal64|SWPAL|__swpal64 de __int64 sin signo (_Target __int64 sin signo, _Value __int64 sin signo)|
|__sys|SYS|int __sys(int, __int64)|
|__svc|SVC|unsigned int __svc(unsigned int, ...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||vacío __writex18byte (sin signo long, unsigned char)|
|__writex18word||vacío __writex18word (sin signo largo, sin signo corto)|
|__writex18dword||vacío __writex18dword (sin firmar largo, sin signo largo)|
|__writex18qword||vacío __writex18qword (sin signo largo, sin signo __int64)|
|__umulh||__umulh \__int64 sin \_signo (_int64 \_sin signo, _int64 sin signo)|
|_CopyDoubleFromInt64||doble _CopyDoubleFromInt64\_(_int64)|
|_CopyFloatFromInt32||flotador\__CopyFloatFromInt32( _int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||int _CountLeadingOnes64 sin \_signo (_int64 sin signo)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||int _CountLeadingSigns64(\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||int _CountLeadingZeros64 sin \_signo (_int64 sin signo)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg(int)|
|_WriteStatusReg|MSR|vacío _WriteStatusReg(int, \__int64)|

[[Volver a la parte superior](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Restricciones de barrera de memoria

Las funciones intrínsecas `__dmb` `__dsb` (barrera de memoria `__isb` de datos), (barrera de sincronización de datos) y (barrera de sincronización de instrucciones) utilizan los siguientes valores predefinidos para especificar la restricción de barrera de memoria en términos del dominio de uso compartido y el tipo de acceso que se ven afectados por la operación.

|Valor de restricción|Descripción|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Todo el sistema, lectura y escritura.|
|_ARM64_BARRIER_ST|Todo el sistema, solo escritura.|
|_ARM64_BARRIER_LD|Sistema completo, de sólo lectura.|
|_ARM64_BARRIER_ISH|Puede compartirse internamente, lectura y escritura.|
|_ARM64_BARRIER_ISHST|Puede compartirse internamente, solo escritura.|
|_ARM64_BARRIER_ISHLD|Compartible interior, sólo lectura.|
|_ARM64_BARRIER_NSH|No puede compartirse, lectura y escritura.|
|_ARM64_BARRIER_NSHST|No puede compartirse, solo escritura.|
|_ARM64_BARRIER_NSHLD|No compartible, sólo lectura.|
|_ARM64_BARRIER_OSH|Puede compartirse externamente, lectura y escritura.|
|_ARM64_BARRIER_OSHST|Puede compartirse externamente, solo escritura.|
|_ARM64_BARRIER_OSHLD|Exterior que se puede retar, sólo lectura.|

Para `__isb` el intrínseco, la única restricción que es actualmente válida es _ARM64_BARRIER_SY; todos los demás valores están reservados por la arquitectura.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/tienda intrínseca

Estas funciones intrínsecas realizan explícitamente cargas y almacenes que no están sujetos a optimizaciones del compilador.

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

*Ubicación*\
La dirección de una ubicación de memoria para leer o escribir.

*Valor*\
Valor que se va a escribir en la ubicación de memoria especificada (solo los intrínsecos de almacén).

#### <a name="return-value-load-intrinsics-only"></a>Valor devuelto (solo intrínsecos de carga)

El valor de la ubicación de memoria especificada por *Location*.

#### <a name="remarks"></a>Observaciones

Puede usar `__iso_volatile_load8/16/32/64` los `__iso_volatile_store8/16/32/64` intrínsecos para realizar explícitamente accesos a la memoria que no están sujetos a optimizaciones del compilador. El compilador no puede quitar, synthetize o cambiar el orden relativo de estas operaciones. Sin embargo, no genera barreras de memoria de hardware implícitas. Por lo tanto, el hardware todavía puede reordenar los accesos de memoria observables en varios subprocesos. Más precisamente, estos elementos intrínsecos son equivalentes a las siguientes expresiones compiladas en **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Observe que los intrínsecos tienen punteros volátiles para dar cabida a variables volátiles. Sin embargo, no hay ningún requisito o recomendación para usar punteros volátiles como argumentos. La semántica de estas operaciones es exactamente la misma si se utiliza un tipo normal y no volátil.

Para obtener más información sobre el argumento de línea de comandos **/volatile:iso,** vea [/volatile (interpretación de palabras clave volátiles)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>Compatibilidad con ARM64 para intrínsecos de otras arquitecturas

En la tabla siguiente se enumeran los intrínsecos de otras arquitecturas que se admiten en plataformas ARM64. Cuando el comportamiento de un intrínseco en ARM64 difiere de su comportamiento en otras arquitecturas de hardware, se observan detalles adicionales.

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|vacío __code_seg(const \*char )|
|__debugbreak|_debugbreak \_de __cdecl de vacío (vacío)|
|__fastfail|__declspec(noreturn) \_void _fastfail(unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield(void) **Nota:** En las plataformas ARM64, esta función genera la instrucción YIELD. Esta instrucción indica que el subproceso está realizando una tarea que puede suspenderse temporalmente de la ejecución (por ejemplo, un spinlock) sin afectar negativamente al programa. Permite a la CPU ejecutar otras tareas durante los ciclos de ejecución que, de lo contrario, se desperdiciarían.|
|_AddressOfReturnAddress|vacío \* _AddressOfReturnAddress (vacío)|
|_BitScanForward|unsigned char _BitScanForward(unsigned long \* _Index, unsigned long _Mask)|
|_BitScanForward64|_BitScanForward64 char sin signo \* (_Index largo sin signo, _Mask __int64 sin signo)|
|_BitScanReverse|_BitScanReverse char sin signo \* (sin signo, long _Index, sin signo _Mask largo)|
|_BitScanReverse64|char _BitScanReverse64 sin signo \* (sin signo _Index largo, sin signo __int64 _Mask)|
|_bittest|char _bittest sin signo \*(const largo, largo)|
|_bittest64|char _bittest64(__int64 const \*, __int64)|
|_bittestandcomplement|char sin signo \*_bittestandcomplement (largo, largo)|
|_bittestandcomplement64|char _bittestandcomplement64 sin \*signo(__int64 , __int64)|
|_bittestandreset|char _bittestandreset sin \*signo (largo, largo)|
|_bittestandreset64|char _bittestandreset64 sin \*signo(__int64 , __int64)|
|_bittestandset|char _bittestandset sin \*signo (largo, largo)|
|_bittestandset64|_bittestandset64 char sin \*signo(__int64 , __int64)|
|_byteswap_uint64|_byteswap_uint64 de \__cdecl __int64 \_sin signo (_int64 sin signo)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable(void) **Nota:** En las plataformas ARM64, esta función genera la instrucción `MSR DAIFCLR,#2`; sólo está disponible como intrínseco.|
|_enable|void __cdecl _enable(void) **Nota:** En las plataformas ARM64, esta función genera la instrucción `MSR DAIFSET,#2`; sólo está disponible como intrínseco.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|vacío \* _ReturnAddress (vacío)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|_rotl64 _cdecl \___int64 sin \_signo (_Value _int64 sin signo, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|_rotr64 _cdecl \___int64 sin \_signo (_Value _int64 sin signo, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Volver a la parte superior](#top)]

## <a name="interlocked-intrinsics"></a>Intrínsecos entrelazados

Los intrínsecos entrelazados son un conjunto de intrínsecos que se usan para realizar operaciones atómicas de lectura-modificación-escritura. Algunos de ellos son comunes a todas las plataformas. Se enumeran por separado aquí porque hay un gran número de ellos. Debido a que sus definiciones son en su mayoría redundantes, es más fácil pensar en ellas en términos generales. Sus nombres pueden utilizarse para derivar los comportamientos exactos.

En la tabla siguiente se resume la compatibilidad con ARM64 de los elementos intrínsecos entrelazados que no son de prueba de bits. Cada celda de la tabla corresponde a un nombre que se crea agregando el nombre de la operación de la celda del extremo izquierdo de la fila y el nombre de tipo de la celda de la parte superior de la columna a `_Interlocked`. Por ejemplo, la celda en `Xor` la `8` intersección de `_InterlockedXor8` la fila y la columna corresponde y es totalmente compatible. La mayoría de las funciones admitidas ofrecen estos sufijos opcionales: `_acq`, `_rel` y `_nf`. El sufijo `_acq` indica una semántica de "adquisición" y el sufijo `_rel` indica una semántica de "versión". El `_nf` sufijo o "sin valla" es exclusivo de ARM y ARM64 y se describe en la siguiente sección.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Sumar|None|None|Completo|Completo|None|None|
|And|Completo|Completo|Completo|Completo|None|None|
|CompareExchange|Completo|Completo|Completo|Completo|Completo|Completo|
|Decremento|None|Completo|Completo|Completo|None|None|
|Exchange|Completo|Completo|Completo|Completo|None|Completo|
|ExchangeAdd|Completo|Completo|Completo|Completo|None|None|
|Incremento|None|Completo|Completo|Completo|None|None|
|Or|Completo|Completo|Completo|Completo|None|None|
|Xor|Completo|Completo|Completo|Completo|None|None|

Clave:

- **Completo**: soporta `_acq` `_rel`formularios `_nf` simples, , , y.

- **Ninguno**: No soportado

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf (sin valla) sufijo

El `_nf` sufijo o "sin valla" indica que la operación no se comporta como ningún tipo `_acq`de `_rel`barrera de memoria, a diferencia de las otras tres formas (simple, , y ), que se comportan como algún tipo de barrera. Un posible uso `_nf` de los formularios es mantener un contador de estadísticas que se actualiza mediante varios subprocesos al mismo tiempo, pero cuyo valor no se usa de otro modo mientras se ejecutan varios subprocesos.

### <a name="list-of-interlocked-intrinsics"></a>Lista de intrínsecos entrelazados

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|_InterlockedAdd|_InterlockedAdd largo (_volatile \*largo, largo)|
|_InterlockedAdd64|__int64 _InterlockedAdd64(\_ \*_int64 \_volátil , _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq\_(_int64 volátil \*, \__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf(\_ \*_int64 \_volátil , _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel(\_ \*_int64 \_volátil, _int64)|
|_InterlockedAdd_acq|_InterlockedAdd_acq largo (largo volátil, \*largo)|
|_InterlockedAdd_nf|_InterlockedAdd_nf largo (largo volátil, \*largo)|
|_InterlockedAdd_rel|_InterlockedAdd_rel largo (largo volátil, \*largo)|
|_InterlockedAnd|_InterlockedAnd largo (largo volátil, \*largo)|
|_InterlockedAnd16|_InterlockedAnd16 corto (corto volátil, \*corto)|
|_InterlockedAnd16_acq|_InterlockedAnd16_acq corto (corto volátil, \*corto)|
|_InterlockedAnd16_nf|_InterlockedAnd16_nf corto (corto volátil, \*corto)|
|_InterlockedAnd16_rel|_InterlockedAnd16_rel corto (corto volátil, \*corto)|
|_InterlockedAnd64|__int64 _InterlockedAnd64\_( \* \__int64 volátil , _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\_ \*_int64 \_volátil , _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf(\_ \*_int64 \_volátil , _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel\_( \* \__int64 volátil , _int64)|
|_InterlockedAnd8|char _InterlockedAnd8(char \*volatile , char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char \*volatile , char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf(char \*volatile , char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char \*volatile , char)|
|_InterlockedAnd_acq|_InterlockedAnd_acq largo (largo volátil, \*largo)|
|_InterlockedAnd_nf|_InterlockedAnd_nf largo (largo volátil, \*largo)|
|_InterlockedAnd_rel|_InterlockedAnd_rel largo (largo volátil, \*largo)|
|_InterlockedCompareExchange|_InterlockedCompareExchange de __cdecl \*largo (largo volátil, largo, largo)|
|_InterlockedCompareExchange_acq|_InterlockedCompareExchange_acq largo (largo volátil, \*largo, largo)|
|_InterlockedCompareExchange_nf|_InterlockedCompareExchange_nf largo (largo volátil, \*largo, largo)|
|_InterlockedCompareExchange_rel|_InterlockedCompareExchange_rel largo (largo volátil, \*largo, largo)|
|_InterlockedCompareExchange16|_InterlockedCompareExchange16 corto (corto volátil, \*corto, corto)|
|_InterlockedCompareExchange16_acq|_InterlockedCompareExchange16_acq corto (corto volátil, \*corto, corto)|
|_InterlockedCompareExchange16_nf|_InterlockedCompareExchange16_nf corto (corto volátil, \*corto, corto)|
|_InterlockedCompareExchange16_rel|_InterlockedCompareExchange16_rel corto (corto volátil, \*corto, corto)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64\_ \*(_int64 \_volátil, _int64, \__int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq( \*_int64 \_volátil \_, _int64, _int64)|
|_InterlockedCompareExchange64_nf|\___int64 _InterlockedCompareExchange64_nf( \*_int64 \_volátil \_, _int64, _int64)|
|_InterlockedCompareExchange64_rel|\___int64 _InterlockedCompareExchange64_rel( \*_int64 \_volátil \_, _int64, _int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8(char \*volatile , char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq(char \*volatile , char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char \*volatile , char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char \*volatile , char, char)|
|_InterlockedCompareExchangePointer|vacío \* \* _InterlockedCompareExchangePointer(void \*volatile \*, \*void , void )|
|_InterlockedCompareExchangePointer_acq|vacío \* _InterlockedCompareExchangePointer_acq \* (vacío \* \*volátil \*, vacío , vacío )|
|_InterlockedCompareExchangePointer_nf|vacío \* _InterlockedCompareExchangePointer_nf \* (vacío \* \*volátil \*, vacío , vacío )|
|_InterlockedCompareExchangePointer_rel|vacío \* _InterlockedCompareExchangePointer_rel \* (vacío \* \*volátil \*, vacío , vacío )|
|_InterlockedCompareExchange128|\__InterlockedCompareExchange128 char sin \* signo( \__int64 \__Destination volátil, \* _ExchangeHigh _int64, _ExchangeLow _int64 _int64 \__ComparandResult)|
|_InterlockedCompareExchange128_acq|\__InterlockedCompareExchange128_acq char sin \* signo( \__int64 \__Destination volátil, _ExchangeHigh _int64, _int64 _ExchangeLow _int64 \_ \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|char _InterlockedCompareExchange128_nf sin\_signo ( _int64 \__Destination \_ \* volátil, \* \__ExchangeHigh _int64, _ExchangeLow _int64 _int64 _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char\__InterlockedCompareExchange128_rel( \* _int64 \__Destination \_volátil, \__int64 \* _ExchangeHigh, _int64 _ExchangeLow _int64 _ComparandResult)|
|_InterlockedDecrement|_InterlockedDecrement de __cdecl \*largo (larga volátil)|
|_InterlockedDecrement16|_InterlockedDecrement16 corto (breve volátil) \*|
|_InterlockedDecrement16_acq|_InterlockedDecrement16_acq corto (breve volátil) \*|
|_InterlockedDecrement16_nf|_InterlockedDecrement16_nf cortos (breve volátil) \*|
|_InterlockedDecrement16_rel|_InterlockedDecrement16_rel corto (breve volátil) \*|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64(\_ \*_int64 volatile )|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\_ \*_int64 volátil )|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf(\_ \*_int64 volátil )|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel(\_ \*_int64 volátil )|
|_InterlockedDecrement_acq|_InterlockedDecrement_acq largo (larga volátil) \*|
|_InterlockedDecrement_nf|_InterlockedDecrement_nf largo (larga volátil) \*|
|_InterlockedDecrement_rel|_InterlockedDecrement_rel largo (larga volátil) \*|
|_InterlockedExchange|_InterlockedExchange de __cdecl \* largo (_Target volátil largo, largo)|
|_InterlockedExchange_acq|_InterlockedExchange_acq largo (_Target volátil \* largo, largo)|
|_InterlockedExchange_nf|_InterlockedExchange_nf largo (_Target volátil \* largo, largo)|
|_InterlockedExchange_rel|_InterlockedExchange_rel largo (_Target volátil \* largo, largo)|
|_InterlockedExchange16|_InterlockedExchange16 corto (_Target volátil \* corto, corto)|
|_InterlockedExchange16_acq|_InterlockedExchange16_acq cortos (_Target volátiles \* cortos, cortos)|
|_InterlockedExchange16_nf|_InterlockedExchange16_nf corto (_Target volátil \* corto, corto)|
|_InterlockedExchange16_rel|_InterlockedExchange16_rel corto (_Target volátil \* corto, corto)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\_ \* _int64 \__Target volátil, _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\_ \* _int64 \__Target volátil, _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\_ \* _int64 \__Target volátil, _int64)|
|_InterlockedExchange64_rel|__int64\__InterlockedExchange64_rel(_int64 \* _Target \_volátil, _int64)|
|_InterlockedExchange8|char _InterlockedExchange8(char \* volatile _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq(char \* volatile _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf(char \* volatile _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel(char \* volatile _Target, char)|
|_InterlockedExchangeAdd|_InterlockedExchangeAdd de __cdecl \*largo (largo volátil, largo)|
|_InterlockedExchangeAdd16|_InterlockedExchangeAdd16 corto (corto volátil, \*corto)|
|_InterlockedExchangeAdd16_acq|_InterlockedExchangeAdd16_acq corto (corto volátil, \*corto)|
|_InterlockedExchangeAdd16_nf|_InterlockedExchangeAdd16_nf corto (corto volátil, \*corto)|
|_InterlockedExchangeAdd16_rel|_InterlockedExchangeAdd16_rel corto (corto volátil, \*corto)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\_ \*_int64 \_volátil , _int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq(\_ \*_int64 \_volátil, _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\_ \*_int64 \_volátil , _int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel(\_ \*_int64 \_volátil , _int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char \*volatile , char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char \*volatile , char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char \*volatile , char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char \*volatile , char)|
|_InterlockedExchangeAdd_acq|_InterlockedExchangeAdd_acq largo (largo volátil, \*largo)|
|_InterlockedExchangeAdd_nf|_InterlockedExchangeAdd_nf largo (largo volátil, \*largo)|
|_InterlockedExchangeAdd_rel|_InterlockedExchangeAdd_rel largo (largo volátil, \*largo)|
|_InterlockedExchangePointer|vacío \* _InterlockedExchangePointer(_Target \* volátil \*esana, \* vacío)|
|_InterlockedExchangePointer_acq|vacío \* \* _InterlockedExchangePointer_acq(vacío \* _Target \*volátil, vacío )|
|_InterlockedExchangePointer_nf|vacío \* _InterlockedExchangePointer_nf(_Target \* volátil \*vacío, \* vacío )|
|_InterlockedExchangePointer_rel|vacío \* \* _InterlockedExchangePointer_rel(vacío \* _Target \*volátil, void )|
|_InterlockedIncrement|_InterlockedIncrement de __cdecl \*largo (larga volátil)|
|_InterlockedIncrement16|_InterlockedIncrement16 corto (breve volátil) \*|
|_InterlockedIncrement16_acq|_InterlockedIncrement16_acq cortos (breve volátil) \*|
|_InterlockedIncrement16_nf|_InterlockedIncrement16_nf corto (breve volátil) \*|
|_InterlockedIncrement16_rel|_InterlockedIncrement16_rel corto (breve volátil) \*|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64(\_ \*_int64 volátil )|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\_ \*_int64 volátil )|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\_ \*_int64 volátil )|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel(\_ \*_int64 volátil )|
|_InterlockedIncrement_acq|_InterlockedIncrement_acq largo (larga volátil) \*|
|_InterlockedIncrement_nf|_InterlockedIncrement_nf largo (larga volátil) \*|
|_InterlockedIncrement_rel|_InterlockedIncrement_rel largo (larga volátil) \*|
|_InterlockedOr|_InterlockedOr largo (largo volátil, \*largo)|
|_InterlockedOr16|_InterlockedOr16 corto (corto volátil, \*corto)|
|_InterlockedOr16_acq|_InterlockedOr16_acq corto (corto volátil, \*corto)|
|_InterlockedOr16_nf|_InterlockedOr16_nf corto (corto volátil, \*corto)|
|_InterlockedOr16_rel|_InterlockedOr16_rel corto (corto volátil, \*corto)|
|_InterlockedOr64|__int64 _InterlockedOr64(\_ \*_int64 \_volátil , _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\_ \*_int64 \_volátil , _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf(\_ \*_int64 \_volátil, _int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel\_( \* \__int64 volátil , _int64)|
|_InterlockedOr8|char _InterlockedOr8(char \*volatile , char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq(char \*volatile , char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf(char \*volatile , char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char \*volatile , char)|
|_InterlockedOr_acq|_InterlockedOr_acq largo (largo volátil, \*largo)|
|_InterlockedOr_nf|_InterlockedOr_nf largo (largo volátil, \*largo)|
|_InterlockedOr_rel|_InterlockedOr_rel largo (largo volátil, \*largo)|
|_InterlockedXor|_InterlockedXor largo (largo volátil, \*largo)|
|_InterlockedXor16|_InterlockedXor16 corto (corto volátil, \*corto)|
|_InterlockedXor16_acq|_InterlockedXor16_acq corto (corto volátil, \*corto)|
|_InterlockedXor16_nf|_InterlockedXor16_nf corto (corto volátil, \*corto)|
|_InterlockedXor16_rel|_InterlockedXor16_rel corto (corto volátil, \*corto)|
|_InterlockedXor64|__int64 _InterlockedXor64(\_ \*_int64 \_volátil , _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq\_( \* \__int64 volátil , _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf(\_ \*_int64 \_volátil, _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel(\_ \*_int64 \_volátil , _int64)|
|_InterlockedXor8|char _InterlockedXor8(char \*volatile , char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char \*volatile , char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char \*volatile , char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char \*volatile , char)|
|_InterlockedXor_acq|_InterlockedXor_acq largo (largo volátil, \*largo)|
|_InterlockedXor_nf|_InterlockedXor_nf largo (largo volátil, \*largo)|
|_InterlockedXor_rel|_InterlockedXor_rel largo (largo volátil, \*largo)|

[[Volver a la parte superior](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest intrínsecos

Los elementos intrínsecos de prueba de bits entrelazados simple son comunes a todas las plataformas. ARM64 agrega `_acq` `_rel`, `_nf` , y variantes, que simplemente modifican la semántica de barrera de una operación, como se describe en [_nf sufijo (sin valla) Sufijo](#nf_suffix) anteriormente en este artículo.

|Nombre de la función|Prototipo de función|
|-------------------|------------------------|
|_interlockedbittestandreset|char _interlockedbittestandreset sin \*signo (largo volátil, largo)|
|_interlockedbittestandreset_acq|char _interlockedbittestandreset_acq sin \*signo (largo volátil, largo)|
|_interlockedbittestandreset_nf|char _interlockedbittestandreset_nf sin \*signo (largo volátil, largo)|
|_interlockedbittestandreset_rel|char _interlockedbittestandreset_rel sin \*signo (largo volátil, largo)|
|_interlockedbittestandreset64|char _interlockedbittestandreset64 sin \*signo(__int64 volatile , __int64)|
|_interlockedbittestandreset64_acq|char _interlockedbittestandreset64_acq(__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_nf|char _interlockedbittestandreset64_nf sin \*signo (__int64 volátil , __int64)|
|_interlockedbittestandreset64_rel|_interlockedbittestandreset64_rel char sin \*signo (__int64 volátil , __int64)|
|_interlockedbittestandset|char _interlockedbittestandset sin \*signo (largo volátil, largo)|
|_interlockedbittestandset_acq|char _interlockedbittestandset_acq sin \*signo (largo volátil, largo)|
|_interlockedbittestandset_nf|char _interlockedbittestandset_nf sin \*signo (largo volátil, largo)|
|_interlockedbittestandset_rel|char _interlockedbittestandset_rel sin \*signo (largo volátil, largo)|
|_interlockedbittestandset64|char _interlockedbittestandset64 sin \*signo (__int64 volátil , __int64)|
|_interlockedbittestandset64_acq|char _interlockedbittestandset64_acq sin \*signo(__int64 volatile , __int64)|
|_interlockedbittestandset64_nf|char _interlockedbittestandset64_nf sin \*signo (__int64 volátil , __int64)|
|_interlockedbittestandset64_rel|char _interlockedbittestandset64_rel sin \*signo(__int64 volatile , __int64)|

[[Volver a la parte superior](#top)]

## <a name="see-also"></a>Consulte también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Intrínsecos ARM](arm-intrinsics.md)\
[Referencia del ensamblador ARM](../assembler/arm/arm-assembler-reference.md)\
[Referencia de idioma C++](../cpp/cpp-language-reference.md)
