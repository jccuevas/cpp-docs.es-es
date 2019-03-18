---
title: Hacer que un objeto ATL no se pueden crear
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 966c7c1e42cd707726a8ca65bb80914c29ad582e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814506"
---
# <a name="making-an-atl-object-noncreatable"></a>Hacer que un objeto ATL no se pueden crear

Puede cambiar los atributos de un objeto basado en ATL COM para que un cliente no puede crear directamente el objeto. En este caso, el objeto se devuelve a través de una llamada al método en otro objeto en lugar de crear directamente.

## <a name="to-make-an-object-noncreatable"></a>Para crear un objeto

1. Quitar el [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para el objeto. Si desea que el objeto no se pueden crear, pero se puede registrar el control, reemplace OBJECT_ENTRY_AUTO con [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Agregar el [noncreatable](../../windows/noncreatable.md) atributo a la coclase en el archivo. idl. Por ejemplo:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>Vea también

[Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tipos de proyecto de Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)
