Experiment 1.1

Contains Duplicate II
class Solution { public: bool containsNearbyDuplicate(vector& nums, int k) { unordered_map<int, int> mp;

    for (int i = 0; i < nums.size(); i++) {
        if (mp.count(nums[i]) && i - mp[nums[i]] <= k)
            return true;

        mp[nums[i]] =i;
    
    }

    return false;
}
};

Experiment 1.2

Search Insert Position
class Solution { public: int searchInsert(vector& nums, int target) { int left = 0; int right = nums.size() - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target) {
            return mid;
        }
        else if (nums[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }

    return left;
}
};

Experiment 1.3

Implement Queue using Stacks
class MyQueue { public: stack input; stack output;

MyQueue() {
}

void push(int x) {
    input.push(x);
}

int pop() {

    if (output.empty()) {
        while (!input.empty()) {
            output.push(input.top());
            input.pop();
        }
    }

    int ans = output.top();
    output.pop();
    return ans;
}

int peek() {

    if (output.empty()) {
        while (!input.empty()) {
            output.push(input.top());
            input.pop();
        }
    }

    return output.top();
}

bool empty() {
    return input.empty() && output.empty();
}
};

Experiment 1.4

Palindrome Linked List
class Solution { public: bool isPalindrome(ListNode* head) { if (head == nullptr || head->next == nullptr) return true;

  
    ListNode* slow = head;
    ListNode* fast = head;

    while (fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
    }

  
    ListNode* prev = nullptr;
    ListNode* curr = slow;

    while (curr != nullptr) {
        ListNode* next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = 
        
    ListNode* left = head;
    ListNode* right = prev;

    while (right != nullptr) {
        if (left->val != right->val)
            return false;

        left = left->next;
        right = right->next;
    }

    return true;
}
}; }
