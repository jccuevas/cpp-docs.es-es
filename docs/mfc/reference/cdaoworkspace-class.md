---
title: Clase CDaoWorkspace
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: 52aaa4970ef483988194691eb6b870cbfe51f494
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377112"
---
# <a name="cdaoworkspace-class"></a>Clase CDaoWorkspace

Administra una sesión de base de datos con nombre, protegida mediante contraseña de inicio de sesión a cierre de sesión, por un único usuario. DAO se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

## <a name="syntax"></a>Sintaxis

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Construye un objeto de área de trabajo. Después, `Create` llame `Open`o .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|Anexa un área de trabajo recién creada a la colección Workspaces del motor de base de datos.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Comienza una nueva transacción, que se aplica a todas las bases de datos abiertas en el área de trabajo.|
|[CDaoWorkspace::Cerrar](#close)|Cierra el espacio de trabajo y todos los objetos que contiene. Las transacciones pendientes se revierten.|
|[CDaoWorkspace::CommitTrans](#committrans)|Completa la transacción actual y guarda los cambios.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Compacta (o duplica) una base de datos.|
|[CDaoWorkspace::Crear](#create)|Crea un nuevo objeto de área de trabajo DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Devuelve el número de objetos de base de datos DAO en la colección Databases del área de trabajo.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Devuelve información sobre una base de datos DAO especificada definida en la colección Databases del área de trabajo.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Devuelve la ubicación de la configuración de inicialización del motor de base de datos Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Devuelve un valor que indica si varias transacciones que implican el mismo origen de datos ODBC se aíslan mediante varias conexiones forzadas al origen de datos.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Devuelve el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar sesión en una base de datos ODBC.|
|[CDaoWorkspace::GetName](#getname)|Devuelve el nombre definido por el usuario para el objeto de área de trabajo.|
|[CDaoWorkspace::GetUserName](#getusername)|Devuelve el nombre de usuario especificado cuando se creó el área de trabajo. Este es el nombre del propietario del área de trabajo.|
|[CDaoWorkspace::GetVersion](#getversion)|Devuelve una cadena que contiene la versión del motor de base de datos asociado al área de trabajo.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Devuelve el número de objetos de área de trabajo DAO en la colección Workspaces del motor de base de datos.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Devuelve información sobre un área de trabajo DAO especificada definida en la colección Workspaces del motor de base de datos.|
|[CDaoWorkspace::Idle](#idle)|Permite que el motor de base de datos realice tareas en segundo plano.|
|[CDaoWorkspace::IsOpen](#isopen)|Devuelve distinto de cero si el área de trabajo está abierta.|
|[CDaoWorkspace::Abierto](#open)|Abre explícitamente un objeto de área de trabajo asociado con el área de trabajo predeterminada de DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Intenta reparar una base de datos dañada.|
|[CDaoWorkspace::Rollback](#rollback)|Finaliza la transacción actual y no guarda los cambios.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Establece la contraseña que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Establece el nombre de usuario que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Establece la ubicación de la configuración de inicialización del motor de base de datos de Microsoft Jet en el registro de Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Especifica si varias transacciones que implican el mismo origen de datos ODBC se aíslan forzando varias conexiones al origen de datos.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Establece el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar sesión en un origen de datos ODBC.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Apunta al objeto de área de trabajo DAO subyacente.|

## <a name="remarks"></a>Observaciones

En la mayoría de los casos, no necesitará varios espacios de trabajo y no necesitará crear objetos de área de trabajo explícitos; Al abrir objetos de base de datos y conjuntos de registros, utilizan el área de trabajo predeterminada de DAO. Sin embargo, si es necesario, puede ejecutar varias sesiones a la vez mediante la creación de objetos de área de trabajo adicionales. Cada objeto de área de trabajo puede contener varios objetos de base de datos abiertos en su propia colección Databases. En MFC, un área de trabajo es principalmente un administrador de transacciones, especificando un conjunto de bases de datos abiertas en el mismo "espacio de transacciones."

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen un prefijo "CDao". En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. Las clases basadas en DAO tienen acceso a los datos a través del motor de base de datos Microsoft Jet, incluidos los controladores ODBC. También admiten operaciones de lenguaje de definición de datos (DDL), como la creación de bases de datos y la adición de tablas y campos a través de las clases, sin tener que llamar a DAO directamente.

## <a name="capabilities"></a>Capacidades

La `CDaoWorkspace` clase proporciona lo siguiente:

- Acceso explícito, si es necesario, a un área de trabajo predeterminada, creada inicializando el motor de base de datos. Normalmente, el área de trabajo predeterminada de DAO se usa implícitamente mediante la creación de objetos de base de datos y conjunto de registros.

- Espacio de transacciones en el que las transacciones se aplican a todas las bases de datos abiertas en el área de trabajo. Puede crear espacios de trabajo adicionales para administrar espacios de transacciones independientes.

- Una interfaz para muchas propiedades del motor de base de datos Microsoft Jet subyacente (consulte las funciones miembro estáticas). Abrir o crear un área de trabajo, o llamar a una función miembro estática antes de abrir o crear, inicializa el motor de base de datos.

- Acceso a la colección Workspaces del motor de base de datos, que almacena todas las áreas de trabajo activas que se le han anexado. También puede crear y trabajar con áreas de trabajo sin anexarlas a la colección.

## <a name="security"></a>Seguridad

MFC no implementa las colecciones Users y Groups en DAO, que se usan para el control de seguridad. Si necesita esos aspectos de DAO, debe programarlos usted mismo a través de llamadas directas a interfaces DAO. Para obtener más información, véase [la Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Uso

Puede utilizar `CDaoWorkspace` la clase para:

- Abra explícitamente el espacio de trabajo predeterminado.

   Normalmente, el uso del área de trabajo predeterminada es implícito, al abrir nuevos [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objetos. Pero es posible que deba tener acceso a él explícitamente, por ejemplo, para tener acceso a las propiedades del motor de base de datos o a la colección Workspaces. Consulte "Uso implícito del espacio de trabajo predeterminado" a continuación.

- Cree nuevos espacios de trabajo. Llame a [Append](#append) si desea agregarlos a la colección Workspaces.

- Abra un espacio de trabajo existente en la colección Workspaces.

La creación de un nuevo área de trabajo que aún no existe en la colección Workspaces se describe en la función miembro [Create.](#create) Los objetos de espacio de trabajo no se conservan de ninguna manera entre las sesiones del motor datababase. Si la aplicación vincula MFC estáticamente, al finalizar la aplicación se anula la inicialización del motor de base de datos. Si la aplicación se vincula dinámicamente con MFC, el motor de base de datos no se inicializa cuando se descarga el archivo DLL de MFC.

Abrir explícitamente el área de trabajo predeterminada, o abrir un área de trabajo existente en el áreas de trabajo colección, se describe en el [Abrir](#open) función miembro.

Finalice una sesión de área de trabajo cerrando el área de trabajo con la función miembro [Close.](#close) `Close`cierra las bases de datos que no ha cerrado anteriormente, revirtiendo las transacciones no confirmadas.

## <a name="transactions"></a>Transacciones

DAO administra las transacciones en el nivel de área de trabajo; por lo tanto, las transacciones en un área de trabajo con varias bases de datos abiertas se aplican a todas las bases de datos. Por ejemplo, si dos bases de datos tienen actualizaciones no confirmadas y se llama a [CommitTrans](#committrans), se confirman todas las actualizaciones. Si desea limitar las transacciones a una sola base de datos, necesita un objeto de área de trabajo independiente para ella.

## <a name="implicit-use-of-the-default-workspace"></a>Uso implícito del espacio de trabajo predeterminado

MFC utiliza el área de trabajo predeterminada de DAO implícitamente en las siguientes circunstancias:

- Si crea un `CDaoDatabase` nuevo objeto pero no `CDaoWorkspace` lo hace a través de un objeto existente, MFC crea un objeto de área de trabajo temporal automáticamente, que corresponde al área de trabajo predeterminada de DAO. Si lo hace para varias bases de datos, todos los objetos de base de datos están asociados con el área de trabajo predeterminada. Puede tener acceso al área `CDaoDatabase` de trabajo de una base de datos a través de un miembro de datos.

- De forma similar, `CDaoRecordset` si crea un objeto `CDaoDatabase` sin proporcionar un puntero a un objeto, MFC crea un objeto de base de datos temporal y, por extensión, un objeto de área de trabajo temporal. Puede tener acceso a la base de datos de `CDaoRecordset` un conjunto de registros, e indirectamente a su área de trabajo, a través de un miembro de datos.

## <a name="other-operations"></a>Otras operaciones

También se proporcionan otras operaciones de base de datos, como la reparación de una base de datos dañada o la compactación de una base de datos.

Para obtener información sobre cómo llamar a DAO directamente y sobre la seguridad de DAO, consulte [la Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Append

Llame a esta función miembro después de llamar a [crear](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

`Append`anexa un objeto de área de trabajo recién creado a la colección Workspaces del motor de base de datos. Los espacios de trabajo no persisten entre las sesiones del motor de base de datos; se almacenan solo en la memoria, no en el disco. No es necesario anexar un espacio de trabajo; si no lo haces, todavía puedes usarlo.

Un área de trabajo anexada permanece en el workspaces colección, en un estado abierto activo, hasta que se llama a su [Close](#close) función miembro.

Para obtener información relacionada, vea el tema "Método de anexar" en la Ayuda de DAO.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDaoWorkspace::BeginTrans

Llame a esta función miembro para iniciar una transacción.

```
void BeginTrans();
```

### <a name="remarks"></a>Observaciones

Después `BeginTrans`de llamar , las actualizaciones que realice en los datos o en la estructura de la base de datos surten efecto al confirmar la transacción. Dado que el área de trabajo define un único espacio de transacciones, la transacción se aplica a todas las bases de datos abiertas del área de trabajo. Hay dos maneras de completar la transacción:

- Llame a la [CommitTrans](#committrans) función miembro para confirmar la transacción y guardar los cambios en el origen de datos.

- O llame a la [Rollback](#rollback) función miembro para cancelar la transacción.

Al cerrar el objeto de área de trabajo o un objeto de base de datos mientras una transacción está pendiente, se revierten todas las transacciones pendientes.

Si necesita aislar transacciones en un origen de datos ODBC de las de otro origen de datos ODBC, vea el [SetIsolateODBCTrans](#setisolateodbctrans) función miembro.

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

Construye un objeto `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto C++, tiene dos opciones:

- Llame a la función miembro [Open](#open) del objeto para abrir el área de trabajo predeterminada o para abrir un objeto existente en la colección Workspaces.

- O llame a la función miembro [Create](#create) del objeto para crear un nuevo objeto de área de trabajo DAO. Esto inicia explícitamente una nueva sesión de `CDaoWorkspace` área de trabajo, a la que puede hacer referencia a través del objeto. Después `Create`de llamar a , puede llamar a [Append](#append) si desea agregar el área de trabajo a la colección Workspaces del motor de base de datos.

Consulte la información general de la clase para [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) para obtener información sobre cuándo necesita crear explícitamente un `CDaoWorkspace` objeto. Normalmente, se usan áreas de trabajo creadas implícitamente al abrir un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto sin especificar un área de trabajo o cuando se abre un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto sin especificar un objeto de base de datos. Los objetos DAO de MFC creados de esta manera usan el área de trabajo predeterminada de DAO, que se crea una vez y se reutiliza.

Para liberar un espacio de trabajo y sus objetos contenidos, llame a la función miembro [Close](#close) del objeto de área de trabajo.

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Cerrar

Llame a esta función miembro para cerrar el objeto de área de trabajo.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Al cerrar un objeto de área de trabajo abierto, se libera el objeto DAO subyacente y, si el área de trabajo es miembro de la colección Workspaces, se quita de la colección. Llamar `Close` es una buena práctica de programación.

> [!CAUTION]
> Al cerrar un objeto de área de trabajo, se cierran las bases de datos abiertas del área de trabajo. Esto da como resultado que los conjuntos de registros abiertos en las bases de datos también se cierren y las ediciones o actualizaciones pendientes se reviertan. Para obtener información relacionada, vea las funciones miembro [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)y [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) .

Los objetos de espacio de trabajo no son permanentes; sólo existen mientras existen referencias a ellos. Esto significa que cuando finaliza la sesión del motor de base de datos, el área de trabajo y su colección Debatono de Bases de Datos no persisten. Debe volver a crearlos para la siguiente sesión abriendo el espacio de trabajo y las bases de datos de nuevo.

Para obtener información relacionada, vea el tema "Método de cierre" en la Ayuda de DAO.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans

Llame a esta función miembro para confirmar una transacción: guarde un grupo de ediciones y actualizaciones en una o varias bases de datos del área de trabajo.

```
void CommitTrans();
```

### <a name="remarks"></a>Observaciones

Una transacción consta de una serie de cambios en los datos de la base de datos o su estructura, comenzando por una llamada a [BeginTrans](#begintrans). Cuando complete la transacción, comprométala o reviertala (cancele los cambios) con [Revertir](#rollback). De forma predeterminada, sin transacciones, las actualizaciones de los registros se confirman inmediatamente. Llamar `BeginTrans` hace que el compromiso de `CommitTrans`las actualizaciones se retrase hasta que llame a .

> [!CAUTION]
> Dentro de un área de trabajo, las transacciones siempre son globales para el área de trabajo y no se limitan a una sola base de datos o conjunto de registros. Si realiza operaciones en más de una base `CommitTrans` de datos o `Rollback` conjunto de registros dentro de una transacción de área de trabajo, confirma todas las actualizaciones pendientes y restaura todas las operaciones en esas bases de datos y conjuntos de registros.

Al cerrar una base de datos o un área de trabajo con transacciones pendientes, todas las transacciones se revierten.

> [!NOTE]
> No se trata de un mecanismo de confirmación de dos fases. Si una actualización no se confirma, otras seguirán compromisentes.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Llame a esta función miembro para compactar un Microsoft Jet especificado (. MDB).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszSrcName*<br/>
El nombre de una base de datos cerrada existente. Puede ser una ruta de acceso completa\\y un nombre de archivo, como "C: .MYDB. MDB". Si el nombre de archivo tiene una extensión, debe especificarla. Si la red es compatible con la convención de nomenclatura uniforme\\\\\\(UNC), también puede especificar una ruta de acceso de red, como por ejemplo, "MYSERVER"\\\\\\. MDB". (Se requieren barras diagonales inversas\\dobles en las cadenas de ruta de acceso porque " " es el carácter de escape C++.)

*lpszDestName*<br/>
La ruta de acceso completa de la base de datos compactada que está creando. También puede especificar una ruta de acceso de red como con *lpszSrcName*. No puede utilizar el argumento *lpszDestName* para especificar el mismo archivo de base de datos que *lpszSrcName*.

*lpszPassword*<br/>
Una contraseña, que se utiliza cuando se desea compactar una base de datos protegida por contraseña. Tenga en cuenta que `CompactDatabase` si utiliza la versión de que toma una contraseña, debe proporcionar todos los parámetros. Además, dado que se trata de un parámetro connect, requiere un formato especial, como se indica a continuación: ; *PWD-lpszPassword*. Por ejemplo: ; PWD"Feliz". (Se requiere el punto y coma inicial.)

*lpszLocale*<br/>
Expresión de cadena utilizada para especificar el orden de intercalación para crear *lpszDestName*. Si omite este argumento aceptando `dbLangGeneral` el valor predeterminado de (véase más adelante), la configuración regional de la nueva base de datos es la misma que la de la base de datos anterior. Los valores posibles son:

- `dbLangGeneral`Inglés, alemán, francés, portugués, italiano y español moderno

- `dbLangArabic`Árabe

- `dbLangCyrillic`Ruso

- `dbLangCzech`Checo

- `dbLangDutch`Holandés

- `dbLangGreek`Griego

- `dbLangHebrew`Hebreo

- `dbLangHungarian`Húngaro

- `dbLangIcelandic`Islandés

- `dbLangNordic`Idiomas nórdicos (solo Microsoft Jet database engine versión 1.0)

- `dbLangNorwdan`Noruego y danés

- `dbLangPolish`Polaco

- `dbLangSpanish`Español Tradicional

- `dbLangSwedfin`Sueco y finlandés

- `dbLangTurkish`Turco

*nOpciones*<br/>
Indica una o más opciones para la base de datos de destino, *lpszDestName*. Si omite este argumento aceptando el valor predeterminado, *lpszDestName* tendrá el mismo cifrado y la misma versión *que lpszSrcName*. Puede combinar `dbEncrypt` la `dbDecrypt` opción u con una de las opciones de versión mediante el operador OR bit a bit. Los valores posibles, que especifican un formato de base de datos, no una versión del motor de base de datos, son:

- `dbEncrypt`Cifre la base de datos durante la compactación.

- `dbDecrypt`Descifre la base de datos mientras se compacta.

- `dbVersion10`Cree una base de datos que use la versión 1.0 del motor de base de datos microsoft Jet durante la compactación.

- `dbVersion11`Cree una base de datos que use la versión 1.1 del motor de base de datos Microsoft Jet durante la compactación.

- `dbVersion20`Cree una base de datos que use la versión 2.0 del motor de base de datos microsoft Jet durante la compactación.

- `dbVersion30`Cree una base de datos que use la versión 3.0 del motor de base de datos de Microsoft Jet durante la compactación.

Puede usar `dbEncrypt` `dbDecrypt` o en el argumento options para especificar si desea cifrar o descifrar la base de datos a medida que se compacta. Si omite una constante de cifrado `dbDecrypt` `dbEncrypt`o si incluye ambos y , *lpszDestName* tendrá el mismo cifrado que *lpszSrcName*. Puede utilizar una de las constantes de versión en el argumento options para especificar la versión del formato de datos de la base de datos compactada. Esta constante solo afecta a la versión del formato de datos de *lpszDestName*. Solo puede especificar una constante de versión. Si omite una constante de versión, *lpszDestName* tendrá la misma versión *que lpszSrcName*. Puede compactar *lpszDestName* solo en una versión que sea igual o posterior a la de *lpszSrcName*.

> [!CAUTION]
> Si una base de datos no está cifrada, es posible, incluso si implementa la seguridad de usuario/contraseña, leer directamente el archivo de disco binario que constituye la base de datos.

### <a name="remarks"></a>Observaciones

A medida que cambia los datos de una base de datos, el archivo de base de datos puede fragmentarse y utilizar más espacio en disco del necesario. Periódicamente, debe compactar la base de datos para desfragmentar el archivo de base de datos. La base de datos compactada suele ser más pequeña. También puede optar por cambiar el orden de intercalación, el cifrado o la versión del formato de datos mientras copia y compacta la base de datos.

> [!CAUTION]
> La `CompactDatabase` función miembro no convertirá correctamente una base de datos completa de Microsoft Access de una versión a otra. Solo se convierte el formato de datos. Los objetos definidos por Microsoft Access, como formularios e informes, no se convierten. Sin embargo, los datos se convierten correctamente.

> [!TIP]
> También puede `CompactDatabase` utilizar para copiar un archivo de base de datos.

Para obtener más información acerca de la compactación de bases de datos, vea el tema "Método CompactDatabase" en la Ayuda de DAO.

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDaoWorkspace::Crear

Llame a esta función miembro para crear un `CDaoWorkspace` nuevo objeto de área de trabajo DAO y asociarlo con el objeto MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Cadena con hasta 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo. Debe proporcionar un nombre. Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

*lpszUserName*<br/>
El nombre de usuario del propietario del área de trabajo. Para conocer los requisitos, vea el parámetro *lpszDefaultUser* para la función miembro [SetDefaultUser.](#setdefaultuser) Para obtener información relacionada, vea el tema "Propiedad UserName" en la Ayuda de DAO.

*lpszPassword*<br/>
La contraseña del nuevo objeto de área de trabajo. Una contraseña puede tener hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (nulo). En las contraseñas se distingue entre mayúsculas y minúsculas. Para obtener información relacionada, vea el tema "Propiedad de contraseña" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

El proceso general de creación es:

1. Construir un [CDaoWorkspace](#cdaoworkspace) objeto.

1. Llame a la `Create` función miembro del objeto para crear el área de trabajo DAO subyacente. Debe especificar un nombre de área de trabajo.

1. Opcionalmente, llame a [Append](#append) si desea agregar el área de trabajo a la colección Workspaces del motor de base de datos. Puede trabajar con el espacio de trabajo sin anexarlo.

Después `Create` de la llamada, el objeto de área de trabajo está en un estado abierto, listo para su uso. No llame `Open` después `Create`de . No se `Create` llama si el área de trabajo ya existe en la colección Workspaces. `Create`inicializa el motor de base de datos si aún no se ha inicializado para la aplicación.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

Llame a esta función miembro para recuperar el número de objetos de base de datos DAO en la colección Databases del área de trabajo: el número de bases de datos abiertas en el área de trabajo.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Valor devuelto

El número de bases de datos abiertas en el área de trabajo.

### <a name="remarks"></a>Observaciones

`GetDatabaseCount`es útil si necesita recorrer en bucle todas las bases de datos definidas en la colección Bases de datos del área de trabajo. Para obtener información sobre una base de datos determinada de la colección, vea [GetDatabaseInfo](#getdatabaseinfo). El uso típico `GetDatabaseCount` es llamar al número de bases de datos abiertas `GetDatabaseInfo`y, a continuación, usar ese número como índice de bucle para las llamadas repetidas a .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Llame a esta función miembro para obtener varios tipos de información sobre una base de datos abierta en el área de trabajo.

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del objeto de base de datos en la colección Databases del área de trabajo, para la búsqueda por índice.

*dbinfo*<br/>
Una referencia a un [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre la base de datos se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva:

- AFX_DAO_PRIMARY_INFO (predeterminado), Actualizable, Transacciones

- AFX_DAO_SECONDARY_INFO información principal más: Versión, Orden de intercalación, Tiempo de espera de consulta

- AFX_DAO_ALL_INFO información primaria y secundaria más: Conectar

*lpszName*<br/>
El nombre del objeto de base de datos, para la búsqueda por nombre. El nombre es una cadena con hasta 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Una versión de la función le permite buscar una base de datos por índice. La otra versión le permite buscar una base de datos por nombre.

Para obtener una descripción de la información devuelta en *dbinfo*, vea el [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para cualquier nivel anterior.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDaoWorkspace::GetIniPath

Llame a esta función miembro para obtener la ubicación de la configuración de inicialización del motor de base de datos Microsoft Jet en el registro de Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la ubicación del registro.

### <a name="remarks"></a>Observaciones

Puede utilizar la ubicación para obtener información sobre la configuración del motor de base de datos. La información devuelta es en realidad el nombre de una subclave del Registro.

Para obtener información relacionada, consulte los temas "IniPath Property" y "Personalización de la configuración del Registro de Windows para el acceso a datos" en la Ayuda de DAO.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Llame a esta función miembro para obtener el valor actual de la propiedad IsolateODBCTrans de DAO para el área de trabajo.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las transacciones ODBC están aisladas; de lo contrario 0.

### <a name="remarks"></a>Observaciones

En algunas situaciones, es posible que deba tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, debe abrir un espacio de trabajo independiente para cada transacción. Tenga en cuenta que aunque cada área de trabajo puede tener su propia conexión ODBC a la base de datos, esto ralentiza el rendimiento del sistema. Dado que el aislamiento de transacciones normalmente no es necesario, las conexiones ODBC desde varios objetos de área de trabajo abiertas por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción a la vez pendiente en una base de datos de este tipo, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo tan pronto como la abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

Para obtener información relacionada, vea el tema "Propiedad IsolateODBCTrans" en la Ayuda de DAO.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Llame a esta función miembro para obtener el valor actual de la propiedad LoginTimeout de DAO para el área de trabajo.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Valor devuelto

El número de segundos antes de que se produzca un error cuando intenta iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Observaciones

Este valor representa el número de segundos antes de que se produzca un error cuando intenta iniciar sesión en una base de datos ODBC. El valor predeterminado de LoginTimeout es 20 segundos. Cuando LoginTimeout se establece en 0, no se produce ningún tiempo de espera y la comunicación con el origen de datos puede dejar de responder.

Cuando intenta iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, la conexión puede producir un error como resultado de errores de red o porque el servidor no se está ejecutando. En lugar de esperar a que se conecten los 20 segundos predeterminados, puede especificar cuánto tiempo espera el motor de base de datos antes de que produzca un error. El inicio de sesión en el servidor se produce implícitamente como parte de una serie de eventos diferentes, como ejecutar una consulta en una base de datos de servidor externo.

Para obtener información relacionada, vea el tema "Propiedad LoginTimeout" en la Ayuda de DAO.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDaoWorkspace::GetName

Llame a esta función miembro para obtener el nombre `CDaoWorkspace` definido por el usuario del objeto de área de trabajo DAO subyacente al objeto.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre definido por el usuario del objeto de área de trabajo DAO.

### <a name="remarks"></a>Observaciones

El nombre es útil para tener acceso al objeto de área de trabajo DAO en la colección Workspaces del motor de base de datos por nombre.

Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>CDaoWorkspace::GetUserName

Llame a esta función miembro para obtener el nombre del propietario del área de trabajo.

```
CString GetUserName();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que representa el propietario del objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Para obtener o establecer los permisos para el propietario del área de trabajo, llame a DAO directamente para comprobar el valor de la propiedad Permisos; esto determina qué permisos tiene el usuario. Para trabajar con permisos, necesita un SISTEMA. MDA.

Para obtener información sobre cómo llamar directamente a DAO, consulte [la Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Para obtener información relacionada, vea el tema "Propiedad UserName" en la Ayuda de DAO.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion

Llame a esta función miembro para determinar la versión del motor de base de datos de Microsoft Jet en uso.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que indica la versión del motor de base de datos asociado con el objeto.

### <a name="remarks"></a>Observaciones

El valor devuelto representa el número de versión con el formato "major.minor"; por ejemplo, "3.0". El número de versión del producto (por ejemplo, 3.0) consta del número de versión (3), un punto y el número de versión (0).

Para obtener información relacionada, vea el tema "Propiedad de versión" en la Ayuda de DAO.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Llame a esta función miembro para recuperar el número de objetos de área de trabajo DAO en el motor de base de datos Workspaces colección.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Valor devuelto

El número de espacios de trabajo abiertos en la colección Espacios de trabajo.

### <a name="remarks"></a>Observaciones

Este recuento no incluye los espacios de trabajo abiertos no anexados a la colección. `GetWorkspaceCount`es útil si necesita recorrer en bucle todos los espacios de trabajo definidos en la colección Workspaces. Para obtener información sobre un área de trabajo determinada de la colección, vea [GetWorkspaceInfo](#getworkspaceinfo). El uso típico `GetWorkspaceCount` es llamar al número de áreas de trabajo abiertas `GetWorkspaceInfo`y, a continuación, usar ese número como índice de bucle para las llamadas repetidas a .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Llame a esta función miembro para obtener varios tipos de información sobre un área de trabajo abierta en la sesión.

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del objeto de base de datos en la colección Workspaces, para la búsqueda por índice.

*wkspcinfo*<br/>
Una referencia a un [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) objeto que devuelve la información solicitada.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el área de trabajo se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva:

- nombre de AFX_DAO_PRIMARY_INFO (predeterminado)

- AFX_DAO_SECONDARY_INFO Información principal más: Nombre de usuario

- AFX_DAO_ALL_INFO información principal y secundaria más: Aislar ODBCTrans

*lpszName*<br/>
El nombre del objeto de área de trabajo, para la búsqueda por nombre. El nombre es una cadena con hasta 14 caracteres que nombra de forma única el nuevo objeto de área de trabajo.

### <a name="remarks"></a>Observaciones

Para obtener una descripción de la información devuelta en *wkspcinfo*, vea el [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para niveles anteriores.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDaoWorkspace::Idle

Llame `Idle` para proporcionar al motor de base de datos la oportunidad de realizar tareas en segundo plano que pueden no estar actualizadas debido al intenso procesamiento de datos.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parámetros

*nAction*<br/>
Una acción que se debe realizar durante el procesamiento inactivo. Actualmente la única `dbFreeLocks`acción válida es .

### <a name="remarks"></a>Observaciones

Esto suele ser cierto en entornos multiusuario y multitarea en los que no hay suficiente tiempo de procesamiento en segundo plano para mantener todos los registros en un conjunto de registros actual.

> [!NOTE]
> No `Idle` es necesario llamar con bases de datos creadas con la versión 3.0 del motor de base de datos Microsoft Jet. Utilícelo `Idle` solo para bases de datos creadas con versiones anteriores.

Normalmente, los bloqueos de lectura se quitan y los datos de los objetos de conjunto de registros de tipo dinámico local se actualizan solo cuando no se producen otras acciones (incluidos los movimientos del mouse). Si llama `Idle`periódicamente, proporcionará al motor de base de datos tiempo para ponerse al día con las tareas de procesamiento en segundo plano mediante la liberación de bloqueos de lectura innecesarios. Especificar la `dbFreeLocks` constante como argumento retrasa el procesamiento hasta que se liberan todos los bloqueos de lectura.

Esta función miembro no es necesaria en entornos de un solo usuario a menos que se estén ejecutando varias instancias de una aplicación. La `Idle` función miembro puede aumentar el rendimiento en un entorno multiusuario porque obliga al motor de base de datos a vaciar los datos en el disco, liberando bloqueos en la memoria. También puede liberar bloqueos de lectura haciendo que las operaciones formen parte de una transacción.

Para obtener información relacionada, vea el tema "Método inactivo" en la Ayuda de DAO.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen

Llame a esta función `CDaoWorkspace` miembro para determinar si el objeto está abierto, es decir, si el objeto MFC se ha inicializado mediante una llamada a [Open](#open) o una llamada a [Create](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de espacio de trabajo está abierto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Puede llamar a cualquiera de las funciones miembro de un área de trabajo que está en un estado abierto.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace

Puntero al objeto de área de trabajo DAO subyacente.

### <a name="remarks"></a>Observaciones

Utilice este miembro de datos si necesita acceso directo al objeto DAO subyacente. Puede llamar a las interfaces del objeto DAO a través de este puntero.

Para obtener información sobre cómo acceder directamente a objetos DAO, consulte [nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDaoWorkspace::Abierto

Abre explícitamente un objeto de área de trabajo asociado con el área de trabajo predeterminada de DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
El nombre del objeto de área de trabajo DAO que se va a abrir: una cadena con hasta 14 caracteres que nombra de forma única el área de trabajo. Acepte el valor predeterminado NULL para abrir explícitamente el área de trabajo predeterminada. Para conocer los requisitos de nomenclatura, consulte el parámetro *lpszName* para [Crear](#create). Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

Después de `CDaoWorkspace` construir un objeto, llame a esta función miembro para realizar una de las siguientes acciones:

- Abra explícitamente el espacio de trabajo predeterminado. Pase NULL para *lpszName*.

- Abra un `CDaoWorkspace` objeto existente, un miembro de la colección Workspaces, por su nombre. Pase un nombre válido para un objeto de área de trabajo existente.

`Open`Coloca el objeto de área de trabajo en un estado abierto y también inicializa el motor de base de datos si aún no se ha inicializado para la aplicación.

Aunque `CDaoWorkspace` solo se pueden llamar a muchas funciones miembro después de abrir el área de trabajo, las siguientes funciones `Open`miembro, que funcionan en el motor de base de datos, están disponibles después de la construcción del objeto C++, pero antes de una llamada a:

||||
|-|-|-|
|[Crear](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Idle](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Llame a esta función miembro si necesita intentar reparar una base de datos dañada que tiene acceso al motor de base de datos de Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
La ruta de acceso y el nombre de archivo de un archivo de base de datos de motor de Microsoft Jet existente. Si omite la ruta de acceso, solo se busca en el directorio actual. Si el sistema admite la convención de nomenclatura uniforme (UNC),\\\\\\también puede\\especificar\\una ruta\\de acceso de red, como: " . MDB". (Se requieren barras diagonales inversas\\dobles en la cadena de ruta de acceso porque " " es el carácter de escape C++.)

### <a name="remarks"></a>Observaciones

Debe cerrar la base de datos especificada por *lpszName* antes de repararla. En un entorno multiusuario, otros usuarios no pueden tener *lpszName* abierto mientras lo está reparando. Si *lpszName* no está cerrado o no está disponible para uso exclusivo, se produce un error.

Esta función miembro intenta reparar una base de datos que se marcó como posiblemente dañada por una operación de escritura incompleta. Esto puede ocurrir si una aplicación que usa el motor de base de datos Microsoft Jet se cierra inesperadamente debido a un corte de energía o un problema de hardware del equipo. Si completa la operación y llama a la [Close](../../mfc/reference/cdaodatabase-class.md#close) función miembro o salir de la aplicación de una manera habitual, la base de datos no se marcará como posiblemente dañada.

> [!NOTE]
> Después de reparar una base de datos, también es una buena idea compactarla mediante la [compactDatabase](#compactdatabase) función miembro para desfragmentar el archivo y recuperar espacio en disco.

Para obtener más información acerca de la reparación de bases de datos, vea el tema "RepairDatabase Method" en la Ayuda de DAO.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDaoWorkspace::Rollback

Llame a esta función miembro para finalizar la transacción actual y restaurar todas las bases de datos en el área de trabajo a su condición antes de que se inició la transacción.

```
void Rollback();
```

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> Dentro de un objeto de área de trabajo, las transacciones siempre son globales para el área de trabajo y no se limitan a una sola base de datos o conjunto de registros. Si realiza operaciones en más de una base `Rollback` de datos o conjunto de registros dentro de una transacción de área de trabajo, restaura todas las operaciones en todas esas bases de datos y conjuntos de registros.

Si cierra un objeto de área de trabajo sin guardar ni revertir ninguna transacción pendiente, las transacciones se revierten automáticamente. Si llama a `Rollback` [CommitTrans](#committrans) o sin llamar primero a [BeginTrans](#begintrans), se produce un error.

> [!NOTE]
> Al iniciar una transacción, el motor de base de datos registra sus operaciones en un archivo guardado en el directorio especificado por la variable de entorno TEMP en la estación de trabajo. Si el archivo de registro de transacciones agota el almacenamiento disponible en `CDaoException` la unidad TEMP, el motor de base de datos hará que MFC produzca un (error DAO 2004). En este punto, `CommitTrans`si se llama a , se confirma un número indeterminado de operaciones, pero se pierden las operaciones no completadas restantes y se debe reiniciar la operación. Al `Rollback` llamar, se libera el registro de transacciones y se revierten todas las operaciones de la transacción.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Llame a esta función miembro para establecer la contraseña predeterminada que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin una contraseña específica.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parámetros

*lpszPassword*<br/>
La contraseña predeterminada. Una contraseña puede tener hasta 14 caracteres y puede contener cualquier carácter excepto ASCII 0 (nulo). En las contraseñas se distingue entre mayúsculas y minúsculas.

### <a name="remarks"></a>Observaciones

La contraseña predeterminada que establezca se aplica a las nuevas áreas de trabajo que cree después de la llamada. Al crear áreas de trabajo posteriores, no es necesario especificar una contraseña en la llamada [Crear.](#create)

Para utilizar esta función miembro:

1. Construir `CDaoWorkspace` un objeto, `Create`pero no llamar a .

1. Llame `SetDefaultPassword` y, si lo desea, [SetDefaultUser](#setdefaultuser).

1. Llame `Create` a este objeto de área de trabajo o los posteriores, sin especificar una contraseña.

De forma predeterminada, la propiedad DefaultUser se establece en "admin" y la propiedad DefaultPassword se establece en una cadena vacía ("").

Para obtener más información acerca de la seguridad, vea el tema "Propiedad de permisos" en la Ayuda de DAO. Para obtener información relacionada, vea los temas "Propiedad DefaultPassword" y "Propiedad DefaultUser" en la Ayuda de DAO.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Llame a esta función miembro para establecer el nombre de usuario predeterminado que utiliza el motor de base de datos cuando se crea un objeto de área de trabajo sin un nombre de usuario específico.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parámetros

*lpszDefaultUser*<br/>
Nombre del usuario predeterminado. Un nombre de usuario puede tener entre 1 y 20 caracteres e incluir caracteres alfabéticos, caracteres acentuados, números, espacios y símbolos, excepto: " (comillas), / (barra diagonal), á (barra diagonal inversa), \[ \] (corchetes), : (colon), &#124; (tubo), \< (signo inferior), > (signo mayor que), + (signo más), signo ( signo igual), ; (punto y coma), , ( \* coma), (signo de interrogación), (asterisco), espacios iniciales y caracteres de control (ASCII 00 a ASCII 31). Para obtener información relacionada, vea el tema "Propiedad UserName" en la Ayuda de DAO.

### <a name="remarks"></a>Observaciones

El nombre de usuario predeterminado que establezca se aplica a las nuevas áreas de trabajo que cree después de la llamada. Al crear áreas de trabajo posteriores, no es necesario especificar un nombre de usuario en la llamada [Create.](#create)

Para utilizar esta función miembro:

1. Construir `CDaoWorkspace` un objeto, `Create`pero no llamar a .

1. Llame `SetDefaultUser` y, si lo desea, [SetDefaultPassword](#setdefaultpassword).

1. Llame `Create` a este objeto de área de trabajo o los posteriores, sin especificar un nombre de usuario.

De forma predeterminada, la propiedad DefaultUser se establece en "admin" y la propiedad DefaultPassword se establece en una cadena vacía ("").

Para obtener información relacionada, vea los temas "Propiedad DefaultUser" y "Propiedad DefaultPassword" en la Ayuda de DAO.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDaoWorkspace::SetIniPath

Llame a esta función miembro para especificar la ubicación de la configuración del registro de Windows para el motor de base de datos Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parámetros

*lpszRegistrySubkey*<br/>
Cadena que contiene el nombre de una subclave del Registro de Windows para la ubicación de la configuración del motor de base de datos de Microsoft Jet o los parámetros necesarios para las bases de datos ISAM instalables.

### <a name="remarks"></a>Observaciones

Llame `SetIniPath` solo si necesita especificar ajustes especiales. Para obtener más información, consulte el tema "IniPath Property" en la Ayuda de DAO.

> [!NOTE]
> Llame `SetIniPath` durante la instalación de la aplicación, no cuando se ejecuta la aplicación. `SetIniPath`debe llamarse antes de abrir cualquier espacio de trabajo, base de datos o conjunto de registros; de lo contrario, MFC produce una excepción.

Puede usar este mecanismo para configurar el motor de base de datos con la configuración del Registro proporcionada por el usuario. El ámbito de este atributo está limitado a la aplicación y no se puede cambiar sin reiniciar la aplicación.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Llame a esta función miembro para establecer el valor de la propiedad IsolateODBCTrans de DAO para el área de trabajo.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parámetros

*bIsolateODBCTrans*<br/>
Pase TRUE si desea comenzar a aislar transacciones ODBC. Pase FALSE si desea dejar de aislar transacciones ODBC.

### <a name="remarks"></a>Observaciones

En algunas situaciones, es posible que deba tener varias transacciones simultáneas pendientes en la misma base de datos ODBC. Para ello, debe abrir un espacio de trabajo independiente para cada transacción. Aunque cada área de trabajo puede tener su propia conexión ODBC a la base de datos, esto ralentiza el rendimiento del sistema. Dado que el aislamiento de transacciones normalmente no es necesario, las conexiones ODBC desde varios objetos de área de trabajo abiertas por el mismo usuario se comparten de forma predeterminada.

Algunos servidores ODBC, como Microsoft SQL Server, no permiten transacciones simultáneas en una sola conexión. Si necesita tener más de una transacción a la vez pendiente en una base de datos de este tipo, establezca la propiedad IsolateODBCTrans en TRUE en cada área de trabajo tan pronto como la abra. Esto fuerza una conexión ODBC independiente para cada área de trabajo.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Llame a esta función miembro para establecer el valor de la propiedad LoginTimeout de DAO para el área de trabajo.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parámetros

*nSeconds*<br/>
El número de segundos antes de que se produzca un error cuando intenta iniciar sesión en una base de datos ODBC.

### <a name="remarks"></a>Observaciones

Este valor representa el número de segundos antes de que se produzca un error cuando intenta iniciar sesión en una base de datos ODBC. El valor predeterminado de LoginTimeout es 20 segundos. Cuando LoginTimeout se establece en 0, no se produce ningún tiempo de espera y la comunicación con el origen de datos puede dejar de responder.

Cuando intenta iniciar sesión en una base de datos ODBC, como Microsoft SQL Server, la conexión puede producir un error como resultado de errores de red o porque el servidor no se está ejecutando. En lugar de esperar a que se conecten los 20 segundos predeterminados, puede especificar cuánto tiempo espera el motor de base de datos antes de que produzca un error. El inicio de sesión en el servidor se produce implícitamente como parte de una serie de eventos diferentes, como ejecutar una consulta en una base de datos de servidor externo. El valor de tiempo de espera viene determinado por la configuración actual de la LoginTimeout propiedad.

Para obtener información relacionada, vea el tema "Propiedad LoginTimeout" en la Ayuda de DAO.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef (clase)](../../mfc/reference/cdaotabledef-class.md)<br/>
[Clase CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Clase CDaoException](../../mfc/reference/cdaoexception-class.md)
