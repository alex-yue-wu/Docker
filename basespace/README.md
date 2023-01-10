## Change user in bs

> change <current_user> to lab@company.com

## Authenticate bs connection

#### establish new auth

```
bs auth
```

#### over write existing auth

```
bs auth --force
```

## download project

```
bs download project -n <project_name> -o /path/to/folder/ --extension=fastq.gz
```

## check current running jobs

```
bs list runs
```
