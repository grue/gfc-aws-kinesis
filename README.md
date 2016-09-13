# gfc-aws-kinesis [![Join the chat at https://gitter.im/gilt/gfc](https://badges.gitter.im/gilt/gfc.svg)](https://gitter.im/gilt/gfc?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
Scala wrapper around AWS Kinesis Client Library


SBT dependency:

```scala
libraryDependencies += "com.gilt" % "gfc-aws-kinesis" % "0.10.0"
```

SBT Akka stream dependency:

```scala
libraryDependencies += "com.gilt" % "gfc-aws-kinesis-akka" % "0.10.0"
```


# Basic usage

Consume events:

```scala

  implicit object ARecordReader extends KinesisRecordReader[A]{
    override def apply(r: Record) : A = {
     // parse A
    }
  }

  val config = DefaultKCLConfiguration("consumer-name", "kinesis-stream-name")

  KCLWorkerRunner(config).runAsyncSingleRecordProcessor[A](1 minute) { a: A =>
     // .. do something with A
  }
```
