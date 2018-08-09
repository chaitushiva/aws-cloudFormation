# aws-cloudFormation
import boto3


def get_log_events(log_group):
    """List the first 10000 log events from a CloudWatch group.

    :param log_group: Name of the CloudWatch log group.

    """
    client = boto3.client('logs')
    resp = client.filter_log_events(logGroupName=log_group, limit=10000)
    return resp['events']


if __name__ == '__main__':
    for event in get_log_events('platform/loris'):
        print(event)
