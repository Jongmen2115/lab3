import subprocess
import json

def send_request(url):
    response = subprocess.run(['curl', '-s', url], capture_output=True, text=True)
    return response

def check_status(response):
    if response.returncode != 0:
        return False, f"Failed to connect: {response.stderr}"
    return True, None

def parse_json(response):
    try:
        data = json.loads(response.stdout)
        return data
    except json.JSONDecodeError as e:
        return None, str(e)

def check_keys(data, keys):
    for key in keys:
        if key not in data:
            return False, f"Key {key} not found"
    return True, None

def run_tests():
    tests = [
        {
            "url": "https://jsonplaceholder.typicode.com/posts/1",
            "required_keys": ["userId", "id", "title", "body"]
        },
        {
            "url": "https://jsonplaceholder.typicode.com/comments/1",
            "required_keys": ["postId", "id", "name", "email", "body"]
        },
        {
            "url": "https://jsonplaceholder.typicode.com/users/1",
            "required_keys": ["id", "name", "username", "email"]
        }
    ]

    for i, test in enumerate(tests):
        print(f"Running Test {i+1}...")
        response = send_request(test['url'])
        
        status_ok, error = check_status(response)
        if not status_ok:
            print(f"Test {i+1}: FAILED - {error}")
            continue
        
        data, error = parse_json(response)
        if data is None:
            print(f"Test {i+1}: FAILED - {error}")
            continue

        keys_ok, error = check_keys(data, test['required_keys'])
        if not keys_ok:
            print(f"Test {i+1}: FAILED - {error}")
        else:
            print(f"Test {i+1}: PASSED")

if __name__ == "__main__":
    run_tests()
