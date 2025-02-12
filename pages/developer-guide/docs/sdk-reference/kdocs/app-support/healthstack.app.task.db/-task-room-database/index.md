---



title: TaskRoomDatabase
permalink: /app-support/healthstack.app.task.db/-task-room-database/index.html



sidebar: dev_doc_sidebar


---



//[app-support](/app-support.html)/[healthstack.app.task.db](../index.html)/[TaskRoomDatabase](index.html)



# TaskRoomDatabase



[androidJvm]\
abstract class [TaskRoomDatabase](index.html) : [RoomDatabase](https://developer.android.com/reference/kotlin/androidx/room/RoomDatabase.html)



## Constructors


| | |
|---|---|
| [TaskRoomDatabase](-task-room-database.html) | [androidJvm]<br>fun [TaskRoomDatabase](-task-room-database.html)() |


## Types


| Name | Summary |
|---|---|
| [Companion](-companion/index.html) | [androidJvm]<br>object [Companion](-companion/index.html) |


## Functions


| Name | Summary |
|---|---|
| [assertNotMainThread](index.html#-917214377%2FFunctions%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP_PREFIX](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP_PREFIX.html)])<br>open fun [assertNotMainThread](index.html#-917214377%2FFunctions%2F-1544593023)() |
| [assertNotSuspendingTransaction](index.html#1166251624%2FFunctions%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [assertNotSuspendingTransaction](index.html#1166251624%2FFunctions%2F-1544593023)() |
| [beginTransaction](index.html#1020009182%2FFunctions%2F-1544593023) | [androidJvm]<br>~~open~~ ~~fun~~ [~~beginTransaction~~](index.html#1020009182%2FFunctions%2F-1544593023)~~(~~~~)~~ |
| [clearAllTables](index.html#404244410%2FFunctions%2F-1544593023) | [androidJvm]<br>@[WorkerThread](https://developer.android.com/reference/kotlin/androidx/annotation/WorkerThread.html)<br>abstract fun [clearAllTables](index.html#404244410%2FFunctions%2F-1544593023)() |
| [close](index.html#1674273423%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [close](index.html#1674273423%2FFunctions%2F-1544593023)() |
| [compileStatement](index.html#162913197%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [compileStatement](index.html#162913197%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)): [SupportSQLiteStatement](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteStatement.html) |
| [createInvalidationTracker](index.html#1389914857%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>abstract fun [createInvalidationTracker](index.html#1389914857%2FFunctions%2F-1544593023)(): [InvalidationTracker](https://developer.android.com/reference/kotlin/androidx/room/InvalidationTracker.html) |
| [createOpenHelper](index.html#-1164251690%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>abstract fun [createOpenHelper](index.html#-1164251690%2FFunctions%2F-1544593023)(p0: [DatabaseConfiguration](https://developer.android.com/reference/kotlin/androidx/room/DatabaseConfiguration.html)): [SupportSQLiteOpenHelper](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteOpenHelper.html) |
| [endTransaction](index.html#622722960%2FFunctions%2F-1544593023) | [androidJvm]<br>~~open~~ ~~fun~~ [~~endTransaction~~](index.html#622722960%2FFunctions%2F-1544593023)~~(~~~~)~~ |
| [getAutoMigrations](index.html#252715599%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [getAutoMigrations](index.html#252715599%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [MutableMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/index.html)&lt;[Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;out [AutoMigrationSpec](https://developer.android.com/reference/kotlin/androidx/room/migration/AutoMigrationSpec.html)&gt;, [AutoMigrationSpec](https://developer.android.com/reference/kotlin/androidx/room/migration/AutoMigrationSpec.html)&gt;): [MutableList](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/index.html)&lt;[Migration](https://developer.android.com/reference/kotlin/androidx/room/migration/Migration.html)&gt; |
| [getBackingFieldMap](index.html#-851261044%2FFunctions%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [getBackingFieldMap](index.html#-851261044%2FFunctions%2F-1544593023)(): [MutableMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/index.html)&lt;[String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), [Any](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-any/index.html)&gt; |
| [getCloseLock](index.html#-1597934906%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [getCloseLock](index.html#-1597934906%2FFunctions%2F-1544593023)(): [Lock](https://developer.android.com/reference/kotlin/java/util/concurrent/locks/Lock.html) |
| [getInvalidationTracker](index.html#-1572952849%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [getInvalidationTracker](index.html#-1572952849%2FFunctions%2F-1544593023)(): [InvalidationTracker](https://developer.android.com/reference/kotlin/androidx/room/InvalidationTracker.html) |
| [getOpenHelper](index.html#528322745%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [getOpenHelper](index.html#528322745%2FFunctions%2F-1544593023)(): [SupportSQLiteOpenHelper](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteOpenHelper.html) |
| [getQueryExecutor](index.html#1823899982%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [getQueryExecutor](index.html#1823899982%2FFunctions%2F-1544593023)(): [Executor](https://developer.android.com/reference/kotlin/java/util/concurrent/Executor.html) |
| [getRequiredAutoMigrationSpecs](index.html#1623281881%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [getRequiredAutoMigrationSpecs](index.html#1623281881%2FFunctions%2F-1544593023)(): [MutableSet](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-set/index.html)&lt;[Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;out [AutoMigrationSpec](https://developer.android.com/reference/kotlin/androidx/room/migration/AutoMigrationSpec.html)&gt;&gt; |
| [getRequiredTypeConverters](index.html#204249253%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [getRequiredTypeConverters](index.html#204249253%2FFunctions%2F-1544593023)(): [MutableMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/index.html)&lt;[Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;*&gt;, [MutableList](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/index.html)&lt;[Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;*&gt;&gt;&gt; |
| [getSuspendingTransactionId](index.html#2127040246%2FFunctions%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>open fun [getSuspendingTransactionId](index.html#2127040246%2FFunctions%2F-1544593023)(): [ThreadLocal](https://developer.android.com/reference/kotlin/java/lang/ThreadLocal.html)&lt;[Int](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/index.html)&gt; |
| [getTransactionExecutor](index.html#139460856%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [getTransactionExecutor](index.html#139460856%2FFunctions%2F-1544593023)(): [Executor](https://developer.android.com/reference/kotlin/java/util/concurrent/Executor.html) |
| [getTypeConverter](index.html#-1472154772%2FFunctions%2F-1544593023) | [androidJvm]<br>@[Nullable](https://developer.android.com/reference/kotlin/androidx/annotation/Nullable.html)<br>open fun &lt;[T](index.html#-1472154772%2FFunctions%2F-1544593023) : [Any](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-any/index.html)&gt; [getTypeConverter](index.html#-1472154772%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;[T](index.html#-1472154772%2FFunctions%2F-1544593023)&gt;): [T](index.html#-1472154772%2FFunctions%2F-1544593023)? |
| [init](index.html#1039887154%2FFunctions%2F-1544593023) | [androidJvm]<br>@[CallSuper](https://developer.android.com/reference/kotlin/androidx/annotation/CallSuper.html)<br>open fun [init](index.html#1039887154%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [DatabaseConfiguration](https://developer.android.com/reference/kotlin/androidx/room/DatabaseConfiguration.html)) |
| [internalInitInvalidationTracker](index.html#11707031%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [internalInitInvalidationTracker](index.html#11707031%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [SupportSQLiteDatabase](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteDatabase.html)) |
| [inTransaction](index.html#-1889647314%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [inTransaction](index.html#-1889647314%2FFunctions%2F-1544593023)(): [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isOpen](index.html#-277138657%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [isOpen](index.html#-277138657%2FFunctions%2F-1544593023)(): [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [query](index.html#-2073828541%2FFunctions%2F-1544593023) | [androidJvm]<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [query](index.html#-2073828541%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [SupportSQLiteQuery](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteQuery.html)): [Cursor](https://developer.android.com/reference/kotlin/android/database/Cursor.html)<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [query](index.html#604106995%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [SupportSQLiteQuery](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteQuery.html), @[Nullable](https://developer.android.com/reference/kotlin/androidx/annotation/Nullable.html)p1: [CancellationSignal](https://developer.android.com/reference/kotlin/android/os/CancellationSignal.html)?): [Cursor](https://developer.android.com/reference/kotlin/android/database/Cursor.html)<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>open fun [query](index.html#-1778261672%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), @[Nullable](https://developer.android.com/reference/kotlin/androidx/annotation/Nullable.html)p1: [Array](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-array/index.html)&lt;[Any](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-any/index.html)&gt;?): [Cursor](https://developer.android.com/reference/kotlin/android/database/Cursor.html) |
| [runInTransaction](index.html#1063989044%2FFunctions%2F-1544593023) | [androidJvm]<br>open fun [runInTransaction](index.html#1063989044%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [Runnable](https://developer.android.com/reference/kotlin/java/lang/Runnable.html))<br>open fun &lt;[V](index.html#1107088127%2FFunctions%2F-1544593023) : [Any](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-any/index.html)&gt; [runInTransaction](index.html#1107088127%2FFunctions%2F-1544593023)(@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)p0: [Callable](https://developer.android.com/reference/kotlin/java/util/concurrent/Callable.html)&lt;[V](index.html#1107088127%2FFunctions%2F-1544593023)&gt;): [V](index.html#1107088127%2FFunctions%2F-1544593023) |
| [setTransactionSuccessful](index.html#954356125%2FFunctions%2F-1544593023) | [androidJvm]<br>~~open~~ ~~fun~~ [~~setTransactionSuccessful~~](index.html#954356125%2FFunctions%2F-1544593023)~~(~~~~)~~ |
| [taskDao](task-dao.html) | [androidJvm]<br>abstract fun [taskDao](task-dao.html)(): [TaskDao](../../healthstack.app.task.dao/-task-dao/index.html) |


## Properties


| Name | Summary |
|---|---|
| [mAutoMigrationSpecs](index.html#-218372351%2FProperties%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP.html)])<br>@[NonNull](https://developer.android.com/reference/kotlin/androidx/annotation/NonNull.html)<br>val [mAutoMigrationSpecs](index.html#-218372351%2FProperties%2F-1544593023): [MutableMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/index.html)&lt;[Class](https://developer.android.com/reference/kotlin/java/lang/Class.html)&lt;out [AutoMigrationSpec](https://developer.android.com/reference/kotlin/androidx/room/migration/AutoMigrationSpec.html)&gt;, [AutoMigrationSpec](https://developer.android.com/reference/kotlin/androidx/room/migration/AutoMigrationSpec.html)&gt; |
| [mCallbacks](index.html#1144805490%2FProperties%2F-1544593023) | [androidJvm]<br>@[RestrictTo](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.html)(value = [[RestrictTo.Scope.LIBRARY_GROUP_PREFIX](https://developer.android.com/reference/kotlin/androidx/annotation/RestrictTo.Scope.LIBRARY_GROUP_PREFIX.html)])<br>@[Nullable](https://developer.android.com/reference/kotlin/androidx/annotation/Nullable.html)<br>~~val~~ [~~mCallbacks~~](index.html#1144805490%2FProperties%2F-1544593023)~~:~~ [MutableList](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/index.html)&lt;[RoomDatabase.Callback](https://developer.android.com/reference/kotlin/androidx/room/RoomDatabase.Callback.html)&gt;? |
| [mDatabase](index.html#-1772608385%2FProperties%2F-1544593023) | [androidJvm]<br>~~val~~ [~~mDatabase~~](index.html#-1772608385%2FProperties%2F-1544593023)~~:~~ [SupportSQLiteDatabase](https://developer.android.com/reference/kotlin/androidx/sqlite/db/SupportSQLiteDatabase.html) |
| [mWriteAheadLoggingEnabled](index.html#1724433270%2FProperties%2F-1544593023) | [androidJvm]<br>val [mWriteAheadLoggingEnabled](index.html#1724433270%2FProperties%2F-1544593023): [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |



