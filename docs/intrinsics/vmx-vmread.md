---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219433"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Específicos de Microsoft**

Lee un campo especificado de la estructura de control de máquina virtual (VMCS) actual y lo coloca en la ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>Parámetros

*Campo*\
de El campo VMCS que se va a leer.

*Valorcampo*\
de Puntero a la ubicación donde se va a almacenar el valor leído del campo VMCS especificado por `Field` el parámetro.

## <a name="return-value"></a>Valor devuelto

|Valor|Significado|
|-----------|-------------|
|0|La operación se realizó correctamente.|
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|
|2|Error en la operación sin estado disponible.|

## <a name="remarks"></a>Comentarios

La función `__vmx_vmread` equivale a la instrucción máquina `VMREAD` . El valor del `Field` parámetro es un índice de campo codificado que se describe en la documentación de Intel. Para obtener más información, busque el Apéndice C de "Intel Virtualization Technical Specification for the IA-32 Intel Architecture", en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmread`|x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
