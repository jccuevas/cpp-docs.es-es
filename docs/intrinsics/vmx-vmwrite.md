---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219392"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Específicos de Microsoft**

Escribe el valor especificado en el campo especificado de la estructura de control de máquina virtual (VMCS) actual.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>Parámetros

*Campo*\
de El campo VMCS que se va a escribir.

*Valorcampo*\
de Valor que se va a escribir en el campo VMCS.

## <a name="return-value"></a>Valor devuelto

0\
La operación se realizó correctamente.

1\
Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.

2\
Error en la operación sin estado disponible.

## <a name="remarks"></a>Comentarios

La función `__vmx_vmwrite` equivale a la instrucción máquina `VMWRITE` . El valor del `Field` parámetro es un índice de campo codificado que se describe en la documentación de Intel. Para obtener más información, busque el Apéndice C de "Intel Virtualization Technical Specification for the IA-32 Intel Architecture", en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmwrite`|x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
